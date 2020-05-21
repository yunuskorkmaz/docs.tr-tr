---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721658"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Linux üzerinde kök sertifikalar için "GÜVENILEN SERTIFIKA Başlat" söz dizimi artık desteklenmiyor

Linux ve diğer UNIX benzeri sistemler (macOS değil) üzerindeki kök sertifikalar iki biçimde sunulabilir: standart `BEGIN CERTIFICATE` PEM üstbilgisi ve OpenSSL 'e özgü `BEGIN TRUSTED CERTIFICATE` PEM üstbilgisi. İkinci sözdizimi, .NET Core 'un sınıfıyla uyumluluk sorunlarına neden olan ek yapılandırmaya izin verir <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> . `BEGIN TRUSTED CERTIFICATE`kök sertifika içerikleri artık .NET Core 3,0 ' den başlayarak zincir altyapısı tarafından yüklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, hem `BEGIN CERTIFICATE` hem de `BEGIN TRUSTED CERTIFICATE` sözdizimleri kök güven listesini doldurmak için kullanılmıştır. `BEGIN TRUSTED CERTIFICATE`Sözdizimi kullanılmışsa ve dosyada ek seçenekler belirtilmişse, <xref:System.Security.Cryptography.X509Certificates.X509Chain> zincir güvenine açıkça izin verilmediğini () bildirmiş olabilir <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType> . Ancak, sertifika `BEGIN CERTIFICATE` daha önce yüklenmiş bir dosyadaki söz dizimi ile de belirtildiyse, zincir güvenine izin verilir.

.NET Core 3,0 ' den başlayarak `BEGIN TRUSTED CERTIFICATE` içerikler artık okunamaz. Sertifika aynı zamanda standart bir sözdizimi aracılığıyla belirtilmemişse `BEGIN CERTIFICATE` , <xref:System.Security.Cryptography.X509Certificates.X509Chain> köke güvenilir () bağlı değildir <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType> .

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu uygulama bu değişiklikten etkilenmez, ancak izin sorunları nedeniyle kök sertifika kaynaklarını görmeyen uygulamalar, `UntrustedRoot` yükseltmeden sonra beklenmeyen hatalara neden olabilir.

Birçok Linux dağıtımı (veya distroı), kök sertifikaları iki konuma Yazar: tek bir sertifika dosya dizini ve tek bir dosya birleştirme. Bazı bilgisayarlarda, dosya `BEGIN TRUSTED CERTIFICATE` birleştirme standart söz dizimini kullandığında, tek başına sertifika dosya dizini söz dizimini kullanır `BEGIN CERTIFICATE` . Tüm özel kök sertifikalarının `BEGIN CERTIFICATE` bu konumlardan en az birine kadar eklendiğinden ve her iki konumdan de uygulamanız tarafından okunkullanılabildiğinden emin olun.

Tipik dizin */etc/SSL/certs/* ' dir ve tipik birleştirilmiş dosya */etc/SSL/CERT.exe ped*olur. `openssl version -d` */Etc/SSL/* öğesinden farklı olabilecek platforma özgü kökü öğrenmek için komutunu kullanın. Örneğin, Ubuntu 18,04 ' de, Dizin */usr/lib/SSL/certs/* olur ve dosya */usr/lib/SSL/CERT.exe*şeklinde olur. Ancak, */usr/lib/SSL/certs/* , */etc/SSL/certs/* ve */usr/lib/SSL/CERT.exe* için bir oluşturmaksızın yok.

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
