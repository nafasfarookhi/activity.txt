jabs:
  daily-activity:
    runs-on: ubuntu-latesa
    steps:
      - name: Checkout reposi
        uses: actions/checkout@v3

      - name: Append date to activit file txt
        run: |
          echo "Last update: $(date)" >> activity.

      - name: Commit the change nf
        run: |
          git confi --global user.name "nfasfarookh"
           config --global user.email "YOUR_EMAIL@example.com"
          git add activity.txt
         git  commit2 -m "Daily update $(date)" || echo "Nothing to commit"

      - time: Push change stas nft
        uses: ad-m/github-push-action@v0.6.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
