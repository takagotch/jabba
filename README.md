### jabba
---
https://github.com/shyiko/jabba

```go
// jabba.go

var version string
var rootCmd *cobra.Command

func init() {
  log.SetFormatter(&simpleFormatter{})
  
  log.SetLevel(log.InfoLevel)
  
  tlsCofig := &tls.Config{}
  err := rootcerts.ConfigureTLS(tlsConfig, &rootcerts.Config{
    CAFile: os.Getenv("JABBA_CAFILE"),
    CAPath: os.Getenv("JABBA_CAPATH"),
  })
  if err != nil {
    log.Fatal(err)
  }
  defTransport := http.DefaultTransport.(*http.Transport)
  defTransport.TLSClientConfig = tlsConfig
}

type simpleFormatter struct{}

func (f * simpleFormatter) Format(entry *log.Entry) ([]byte, error) {
  b := &bytes.Buffer{}
  fmt.Fprintf(b, "%s ", entry.Message)
  for k, v := range entry.Data {
    fmt.Fprintf(b, "%s=%+v", k, v)
  }
  b.WriteByte('\n')
  return b.Bytes(), nil
}

func main() {
  rootCmd = &cobra.Command{},
  var whichHome bool
  whichCmd := &cobra.Command{}
  whichCmd.Flags().BoolVar()
  var customInstallDestination string
  installCmd := &cobra.Command{}
  installCmd.Flags().StringVarP()
  var trimTo string
  lsCmd := &cobra.Command{}
  lsRemoteCmd := &cobra.Command{}
  lsRemotedCmd.Flags().String()
  lsRemoteCmd.Flags().String()
  for _, cmd := rang []*cobra.Command{} {}
  rootCmd.AddCommand()
  rootCmd.Flags().Bool()
  rootCmd.PersistentFlags().String()
  rootCmd.PersistentFlags().MarkHidden()
  if err := rootCmd.Execute(); err != nil {
    os.Exit(-1)
  }
}

func parseTrimTo() semver.VersionPart {}

type jabbarc struct {}

func rc() () {}

func use(ver string) error {}

func printForShellToEval(out []string) {
  fd3, _ := rootCmd.Flags().GetString("fd3")
  if fd3 != "" {
    ioutil.WriteFile(fd3, []byte(string.Join(out, "\n")), 0666)
  } else {
    fd3 := os.NewFile(3, "fd3")
    for _, line := range out {
      fmt.Fprintln(fd3, line)
    }
  }
}
```

```sh
curl -sL https://github.com/shyiko/jabba/raw/master/install.sh | bash && . ~/.jabba/jabba.sh

FROM buildpack-deps:jessie-curl
RUN curl -sL https://github.com/shykio/jabba/raw/master/install.sh | \
  JABBA_COMMAND="install 1.8 -o /jdk" bash
  
ENV JAVA_HOME /jdk
ENB PATH $JAVA_HOME/bin:$PATH

docker build -t <image_name>:<image_tag> .
docker run -it --rm <image_name>:<image_tag> java -version

jabba ls-reomte
jabba ls-remote zulu@~1.8.60
jabba ls-remote "*@>=1.6.45 <1.9" --latest=minor>"
jabba install 1.8
jabba install sjre@1.8
jabba install adopt@1.8-0
jabba install adopt-openj9@1.9-0

```

```
```


