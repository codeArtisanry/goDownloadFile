# goDownloadFile
download file and store it in CWD, by just passing the file name &amp; URL

### import package in golang file

```
import (github.com/codeArtisan4/goDownloadFile)
```
```
func DownloadFile(URL, fileName string) error {
	//Get the response bytes from the url
	response, err := http.Get(URL)
	if err != nil {
		return err
	}
	defer response.Body.Close()

	if response.StatusCode != 200 {
		return errors.New("Received non 200 response code")
	}
	//Create a empty file
	file, err := os.Create(fileName)
	if err != nil {
		return err
	}
	defer file.Close()

	//Write the bytes to the fiel
	_, err = io.Copy(file, response.Body)
	if err != nil {
		return err
	}

	return nil
}
```


Use directly this Function by 

```
go get github.com/codeArtisan4/goDownloadFile
```
