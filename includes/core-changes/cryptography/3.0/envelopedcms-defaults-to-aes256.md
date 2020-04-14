---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275234"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms varsayılan olarak AES-256 şifrelemesi için

Kullanılan `EnvelopedCms` varsayılan simetrik şifreleme algoritması TripleDES'ten AES-256'ya değiştirildi.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core Preview 7 ve <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> önceki sürümlerinde, bir yapıcı aşırı yük yoluyla simetrik şifreleme algoritması belirtmeden verileri şifrelemek için kullanıldığında, veriler TripleDES/3DES/3DEA/DES3-EDE algoritması ile şifrelenmiştir.

.NET Core 3.0 Preview 8 ile başlayarak [(System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet paketinin 4.6.0 sürümü üzerinden) varsayılan algoritma algoritma modernizasyonu ve varsayılan seçeneklerin güvenliğini artırmak için AES-256 olarak değiştirildi. İleti alıcısı sertifikasında (EC olmayan) diffie-Hellman ortak anahtarı varsa, <xref:System.Security.Cryptography.CryptographicException> şifreleme işlemi temel platformdaki sınırlamalar nedeniyle başarısız olabilir.

Aşağıdaki örnek kodda, .NET Core 3.0 Preview 7 veya daha önce çalışıyorsa veriler TripleDES ile şifrelenir. .NET Core 3.0 Preview 8 veya sonraki saatlerde çalışıyorsa, AES-256 ile şifrelenir.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 8

#### <a name="recommended-action"></a>Önerilen eylem

Değişiklikten olumsuz etkilenirseniz, aşağıdakigibi bir tür <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>parametresi içeren bir oluşturucudaki şifreleme algoritma tanımlayıcısını açıkça belirterek TripleDES şifrelemesini geri yükleyebilirsiniz:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
