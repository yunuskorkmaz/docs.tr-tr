---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237480"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms varsayılan değer AES-256 şifrelemesi

@No__t-0 tarafından kullanılan varsayılan simetrik şifreleme algoritması, TripleDES 'ten AES-256 olarak değiştirilmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core Preview 7 ve önceki sürümlerinde, bir Oluşturucu aşırı yüklemesi aracılığıyla simetrik şifreleme algoritması belirtmeden verileri şifrelemek için <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> kullanıldığında, veriler TripleDES/3DES/3DEA/DES3-ENGELLEYEBILECEK algoritmayla şifrelenir.

.NET Core 3,0 Preview 8 ' den itibaren ( [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet paketinin sürümü 4.6.0 aracılığıyla), varsayılan algoritma, algoritma modernleştirme için AES-256 olarak değiştirilmiştir ve varsayılan seçeneklerin güvenliğini artırır. Bir ileti alıcı sertifikasında (EC olmayan) bir Diffie-Hellman ortak anahtarı varsa, temeldeki platformda sınırlamalar nedeniyle şifreleme işlemi bir <xref:System.Security.Cryptography.CryptographicException> ile başarısız olabilir.

Aşağıdaki örnek kodda, veriler .NET Core 3,0 Preview 7 veya daha önceki sürümlerde çalışıyorsa üç aylık bir şekilde şifrelenir. .NET Core 3,0 Preview 8 veya üzeri sürümlerde çalışıyorsa, AES-256 ile şifrelenir.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Değişiklik tarafından olumsuz bir şekilde etkilenmiyorsanız, şifreleme algoritması tanımlayıcısını, <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> türünde bir parametre içeren bir <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> oluşturucuda açıkça belirterek Üçlü şifrelemeyi geri yükleyebilirsiniz. Örneğin:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Kategori

To

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
