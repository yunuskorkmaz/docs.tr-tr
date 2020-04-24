---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135612"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a><span data-ttu-id="324f6-101">Linux üzerinde kök sertifikalar için "GÜVENILEN SERTIFIKA Başlat" söz dizimi artık desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="324f6-101">"BEGIN TRUSTED CERTIFICATE" syntax no longer supported for root certificates on Linux</span></span>

<span data-ttu-id="324f6-102">Linux ve diğer UNIX benzeri sistemler (macOS değil) üzerindeki kök sertifikalar iki biçimde sunulabilir: standart `BEGIN CERTIFICATE` PEM üstbilgisi ve OpenSSL 'e özgü `BEGIN TRUSTED CERTIFICATE` PEM üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="324f6-102">Root certificates on Linux and other Unix-like systems (but not macOS) can be presented in two forms: the standard `BEGIN CERTIFICATE` PEM header, and the OpenSSL-specific `BEGIN TRUSTED CERTIFICATE` PEM header.</span></span> <span data-ttu-id="324f6-103">İkinci sözdizimi, .NET Core 'un <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> sınıfıyla uyumluluk sorunlarına neden olan ek yapılandırmaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="324f6-103">The latter syntax allows for additional configuration that has caused compatibility issues with .NET Core's <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> class.</span></span> <span data-ttu-id="324f6-104">`BEGIN TRUSTED CERTIFICATE`kök sertifika içerikleri artık .NET Core 3,0 ' den başlayarak zincir altyapısı tarafından yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="324f6-104">`BEGIN TRUSTED CERTIFICATE` root certificate contents are no longer loaded by the chain engine starting in .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="324f6-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="324f6-105">Change description</span></span>

<span data-ttu-id="324f6-106">Daha önce, hem `BEGIN CERTIFICATE` hem `BEGIN TRUSTED CERTIFICATE` de sözdizimleri kök güven listesini doldurmak için kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="324f6-106">Previously, both the `BEGIN CERTIFICATE` and `BEGIN TRUSTED CERTIFICATE` syntaxes were used to populate the root trust list.</span></span> <span data-ttu-id="324f6-107">`BEGIN TRUSTED CERTIFICATE` Sözdizimi kullanılmışsa ve dosyada ek seçenekler belirtilmişse, <xref:System.Security.Cryptography.X509Certificates.X509Chain> zincir güvenine açıkça izin verilmediğini (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>) bildirmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="324f6-107">If the `BEGIN TRUSTED CERTIFICATE` syntax was used and additional options were specified in the file, <xref:System.Security.Cryptography.X509Certificates.X509Chain> may have reported that the chain trust was explicitly disallowed (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span></span> <span data-ttu-id="324f6-108">Ancak, sertifika daha önce yüklenmiş bir dosyadaki `BEGIN CERTIFICATE` söz dizimi ile de belirtildiyse, zincir güvenine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="324f6-108">However, if the certificate was also specified with the `BEGIN CERTIFICATE` syntax in a previously loaded file, the chain trust was allowed.</span></span>

<span data-ttu-id="324f6-109">.NET Core 3,0 ' `BEGIN TRUSTED CERTIFICATE` den başlayarak içerikler artık okunamaz.</span><span class="sxs-lookup"><span data-stu-id="324f6-109">Starting in .NET Core 3.0, `BEGIN TRUSTED CERTIFICATE` contents are no longer read.</span></span> <span data-ttu-id="324f6-110">Sertifika aynı zamanda standart `BEGIN CERTIFICATE` bir sözdizimi aracılığıyla belirtilmemişse, <xref:System.Security.Cryptography.X509Certificates.X509Chain> köke güvenilir (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>) bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="324f6-110">If the certificate is not also specified via a standard `BEGIN CERTIFICATE` syntax, the <xref:System.Security.Cryptography.X509Certificates.X509Chain> reports that the root is not trusted (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="324f6-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="324f6-111">Version introduced</span></span>

<span data-ttu-id="324f6-112">3,0</span><span class="sxs-lookup"><span data-stu-id="324f6-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="324f6-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="324f6-113">Recommended action</span></span>

<span data-ttu-id="324f6-114">Çoğu uygulama bu değişiklikten etkilenmez, ancak izin sorunları nedeniyle kök sertifika kaynaklarını görmeyen uygulamalar, yükseltmeden sonra beklenmeyen `UntrustedRoot` hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="324f6-114">Most applications are unaffected by this change, but applications that cannot see both root certificate sources because of permissions problems may experience unexpected `UntrustedRoot` errors after upgrading.</span></span>

<span data-ttu-id="324f6-115">Birçok Linux dağıtımı (veya distroı), kök sertifikaları iki konuma Yazar: tek bir sertifika dosya dizini ve tek bir dosya birleştirme.</span><span class="sxs-lookup"><span data-stu-id="324f6-115">Many Linux distributions (or distros) write root certificates into two locations: a one-certificate-per-file directory, and a one-file concatenation.</span></span> <span data-ttu-id="324f6-116">Bazı bilgisayarlarda, dosya birleştirme standart `BEGIN TRUSTED CERTIFICATE` `BEGIN CERTIFICATE` söz dizimini kullandığında, tek başına sertifika dosya dizini söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="324f6-116">On some distros, the one-certificate-per-file directory uses the `BEGIN TRUSTED CERTIFICATE` syntax while the file concatenation uses the standard `BEGIN CERTIFICATE` syntax.</span></span> <span data-ttu-id="324f6-117">Tüm özel kök sertifikalarının bu konumlardan en az birine `BEGIN CERTIFICATE` kadar eklendiğinden ve her iki konumdan de uygulamanız tarafından okunkullanılabildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="324f6-117">Ensure that any custom root certificates are added as `BEGIN CERTIFICATE` in at least one of these locations, and that both locations can be read by your application.</span></span>

<span data-ttu-id="324f6-118">Tipik dizin */etc/SSL/certs/* ' dir ve tipik birleştirilmiş dosya */etc/SSL/CERT.exe ped*olur.</span><span class="sxs-lookup"><span data-stu-id="324f6-118">The typical directory is */etc/ssl/certs/* and the typical concatenated file is */etc/ssl/cert.pem*.</span></span> <span data-ttu-id="324f6-119">`openssl version -d` */Etc/SSL/* öğesinden farklı olabilecek platforma özgü kökü öğrenmek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="324f6-119">Use the command `openssl version -d` to determine the platform-specific root, which may differ from */etc/ssl/*.</span></span> <span data-ttu-id="324f6-120">Örneğin, Ubuntu 18,04 ' de, Dizin */usr/lib/SSL/certs/* olur ve dosya */usr/lib/SSL/CERT.exe*şeklinde olur.</span><span class="sxs-lookup"><span data-stu-id="324f6-120">For example, on Ubuntu 18.04, the directory is */usr/lib/ssl/certs/* and the file is */usr/lib/ssl/cert.pem*.</span></span> <span data-ttu-id="324f6-121">Ancak, */usr/lib/SSL/certs/* , */etc/SSL/certs/* ve */usr/lib/SSL/CERT.exe* için bir oluşturmaksızın yok.</span><span class="sxs-lookup"><span data-stu-id="324f6-121">However, */usr/lib/ssl/certs/* is a symlink to */etc/ssl/certs/* and */usr/lib/ssl/cert.pem* does not exist.</span></span>

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

### <a name="category"></a><span data-ttu-id="324f6-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="324f6-122">Category</span></span>

<span data-ttu-id="324f6-123">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="324f6-123">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="324f6-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="324f6-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
