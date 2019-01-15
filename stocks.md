```bash
# NASDAQ stock market data, combine into file
qna() {
  touch NASDAQ.fin && mv NASDAQ.fin NASDAQ.bak && find | grep NASDAQ.*txt | sort | wc -l && qnb
}
export -f qna

qnb() {
  touch NASDAQ.fin && find | grep NASDAQ.*txt | sort | xargs tail -q -n +2 > NASDAQ.fin && wc -l NASDAQ.fin && qnc
}
export -f qnb

qnc() {
  find | grep NASDAQ.*txt | sort | xargs wc -l | tail -n -1
}
export -f qnc

# NYSE stock market data, combine into file
qya() {
  touch NYSE.fin && mv NYSE.fin NYSE.bak && find | grep NYSE.*txt | sort | wc -l && qyb
}
export -f qya

# Count the number of files
qyb() {
  touch NYSE.fin && find | grep NYSE.*txt | sort | xargs tail -q -n +2 > NYSE.fin && wc -l NYSE.fin && qyc
}
export -f qyb

# Write a new file with headers removed
qyc() {
  find | grep NYSE.*txt | sort | xargs wc -l | tail -n -1
}
export -f qyc
```
