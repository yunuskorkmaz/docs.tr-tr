---
ms.openlocfilehash: d23c6cc9f8ee9c912ce5c9509d157692d1a18f90
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721446"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms varsayılan değer AES-256 şifrelemesi

Tarafından kullanılan varsayılan simetrik şifreleme algoritması, `EnvelopedCms` TripleDES 'TEN AES-256 ' e değişmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core Preview 7 ve önceki sürümlerinde, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> bir Oluşturucu aşırı yüklemesi aracılığıyla simetrik şifreleme algoritması belirtmeden verileri şifrelemek için kullanıldığında, veriler TripleDES/3DES/3DEA/DES3-engelleyebilecek algoritmayla şifrelenir.

.NET Core 3,0 Preview 8 ' den itibaren ( [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet paketinin sürümü 4.6.0 aracılığıyla), varsayılan algoritma, algoritma modernleştirme için AES-256 olarak değiştirilmiştir ve varsayılan seçeneklerin güvenliğini artırır. Bir ileti alıcı sertifikasında (EC olmayan) bir Diffie-Hellman ortak anahtarı varsa, <xref:System.Security.Cryptography.CryptographicException> temel platformdaki sınırlamalar nedeniyle şifreleme işlemi başarısız olabilir.

Aşağıdaki örnek kodda, veriler .NET Core 3,0 Preview 7 veya daha önceki sürümlerde çalışıyorsa üç aylık bir şekilde şifrelenir. .NET Core 3,0 Preview 8 veya üzeri sürümlerde çalışıyorsa, AES-256 ile şifrelenir.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Değişiklik tarafından olumsuz bir şekilde etkilenmiyorsanız, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> Bu tür bir parametre içeren bir oluşturucuda, şifreleme algoritması tanımlayıcısını açıkça belirterek TripleDES şifrelemesini geri yükleyebilirsiniz <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> :

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

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
