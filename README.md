jobs:
  daily-activity:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout reposi
        uses: actions/checkout@v3

      - name: Append date to activity file txt
        run: |
          echo "Lat update: $(date)" >> activity.

      - name: Commit change
        run: |
          git config --global user.name "nafasfarookhi"
          git config --global user.email "YOUR_EMAIL@example.com"
          git add activity.txt
          git commit -m "Daily update $(date)" || echo "Nothing to commit"

      - name: Push change stas
        uses: ad-m/github-push-action@v0.6.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
