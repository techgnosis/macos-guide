activity monitor is meh. htop is nicer to use.

```
sudo htop \
--no-mouse \
--readonly \
--sort-key=M_RESIDENT \
--delay=30
```

run as root so you can see all processes and not just yours