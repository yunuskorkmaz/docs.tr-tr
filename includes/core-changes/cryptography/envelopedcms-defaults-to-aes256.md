---
ms.openlocfilehash: b965c3a975b0f2cadd906799fef1665261d96d6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181999"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="adfd6-101">EnvelopedCms varsayılan değer AES-256 şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="adfd6-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="adfd6-102">Tarafından `EnvelopedCms` kullanılan varsayılan simetrik şifreleme algoritması, TripleDES 'ten AES-256 ' e değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="adfd6-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="details"></a><span data-ttu-id="adfd6-103">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="adfd6-103">Details</span></span>

<span data-ttu-id="adfd6-104">.NET Core Preview 7 ve önceki sürümlerinde, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> bir Oluşturucu aşırı yüklemesi aracılığıyla simetrik şifreleme algoritması belirtmeden verileri şifrelemek için kullanıldığında, veriler TripleDES/3DES/3dea/DES3-engelleyebilecek algoritmayla şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="adfd6-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="adfd6-105">.NET Core 3,0 Preview 8 ' den itibaren ( [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet paketinin sürümü 4.6.0 aracılığıyla), varsayılan algoritma, algoritma modernleştirme için AES-256 olarak değiştirilmiştir ve varsayılan seçeneklerin güvenliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="adfd6-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="adfd6-106">Bir ileti alıcı sertifikasında (EC olmayan) bir Diffie-Hellman ortak anahtarı varsa, temel platformdaki sınırlamalar <xref:System.Security.Cryptography.CryptographicException> nedeniyle şifreleme işlemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="adfd6-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="adfd6-107">Aşağıdaki örnek kodda, veriler .NET Core 3,0 Preview 7 veya daha önceki sürümlerde çalışıyorsa üç aylık bir şekilde şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="adfd6-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="adfd6-108">.NET Core 3,0 Preview 8 veya üzeri sürümlerde çalışıyorsa, AES-256 ile şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="adfd6-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="adfd6-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="adfd6-109">Version introduced</span></span>

<span data-ttu-id="adfd6-110">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="adfd6-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="adfd6-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="adfd6-111">Recommended action</span></span>

<span data-ttu-id="adfd6-112">Değişiklik tarafından olumsuz bir şekilde etkilenmiyorsanız, bu tür <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>bir parametre içeren bir oluşturucuda, şifreleme algoritması tanımlayıcısını açıkça belirterek TripleDES şifrelemesini geri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="adfd6-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="adfd6-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="adfd6-113">Category</span></span>

<span data-ttu-id="adfd6-114">To</span><span class="sxs-lookup"><span data-stu-id="adfd6-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="adfd6-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="adfd6-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
