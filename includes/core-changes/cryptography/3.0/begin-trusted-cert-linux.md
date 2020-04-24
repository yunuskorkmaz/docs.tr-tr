---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135612"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Linux üzerinde kök sertifikalar için "GÜVENILEN SERTIFIKA Başlat" söz dizimi artık desteklenmiyor

Linux ve diğer UNIX benzeri sistemler (macOS değil) üzerindeki kök sertifikalar iki biçimde sunulabilir: standart `BEGIN CERTIFICATE` PEM üstbilgisi ve OpenSSL 'e özgü `BEGIN TRUSTED CERTIFICATE` PEM üstbilgisi. İkinci sözdizimi, .NET Core 'un <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> sınıfıyla uyumluluk sorunlarına neden olan ek yapılandırmaya izin verir. `BEGIN TRUSTED CERTIFICATE`kök sertifika içerikleri artık .NET Core 3,0 ' den başlayarak zincir altyapısı tarafından yüklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, hem `BEGIN CERTIFICATE` hem `BEGIN TRUSTED CERTIFICATE` de sözdizimleri kök güven listesini doldurmak için kullanılmıştır. `BEGIN TRUSTED CERTIFICATE` Sözdizimi kullanılmışsa ve dosyada ek seçenekler belirtilmişse, <xref:System.Security.Cryptography.X509Certificates.X509Chain> zincir güvenine açıkça izin verilmediğini (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>) bildirmiş olabilir. Ancak, sertifika daha önce yüklenmiş bir dosyadaki `BEGIN CERTIFICATE` söz dizimi ile de belirtildiyse, zincir güvenine izin verilir.

.NET Core 3,0 ' `BEGIN TRUSTED CERTIFICATE` den başlayarak içerikler artık okunamaz. Sertifika aynı zamanda standart `BEGIN CERTIFICATE` bir sözdizimi aracılığıyla belirtilmemişse, <xref:System.Security.Cryptography.X509Certificates.X509Chain> köke güvenilir (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>) bağlı değildir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu uygulama bu değişiklikten etkilenmez, ancak izin sorunları nedeniyle kök sertifika kaynaklarını görmeyen uygulamalar, yükseltmeden sonra beklenmeyen `UntrustedRoot` hatalara neden olabilir.

Birçok Linux dağıtımı (veya distroı), kök sertifikaları iki konuma Yazar: tek bir sertifika dosya dizini ve tek bir dosya birleştirme. Bazı bilgisayarlarda, dosya birleştirme standart `BEGIN TRUSTED CERTIFICATE` `BEGIN CERTIFICATE` söz dizimini kullandığında, tek başına sertifika dosya dizini söz dizimini kullanır. Tüm özel kök sertifikalarının bu konumlardan en az birine `BEGIN CERTIFICATE` kadar eklendiğinden ve her iki konumdan de uygulamanız tarafından okunkullanılabildiğinden emin olun.

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

### <a name="category"></a>Kategori

Şifreleme

### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
