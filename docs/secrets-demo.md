     # - name: Show base64-encoded secret (leak test) (github fixed this issue)
      #   env:
      #     MY_SECRET: ${{secrets.THE_WORLD}}
      #   run: |
      #     echo -n "$MY_SECRET" | base64
      # - name: Show partial secret (real leak - masking won't catch this)
      #   env:
      #     MY_SECRET: ${{secrets.THE_WORLD}}
      #   run: |
      #     echo "First 2 chars: ${MY_SECRET:0:2}"
      #     echo "2 to last: ${MY_SECRET:2}"
  # check-env-secret:
  #   runs-on: ubuntu-latest
  #   environment: Enji
  #   steps:
  #     - name: Use the env secret
  #       env:
  #         MY_SECRET: ${{secrets.ENV}}
  #       run: |
  #         echo "Environment secret length check:"
  #         echo -n "$MY_SECRET" | wc -c
  # demo-leak-risk:
  #   runs-on: ubuntu-latest
  #   steps:
  #     - name: Write secret into a file(for demo only)
  #       env:
  #         MY_SECRET: ${{secrets.THE_WORLD}}
  #       run: |
  #         echo "$MY_SECRET" > secret_dump.txt
  #     - name: Upload as artifact (this is the leak point)
  #       uses: actions/upload-artifact@v4
  #       with:
  #         name: leaked-file
  #         path: secret_dump.txt
