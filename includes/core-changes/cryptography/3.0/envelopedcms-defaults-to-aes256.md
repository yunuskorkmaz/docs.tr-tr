---
ms.openlocfilehash: d23c6cc9f8ee9c912ce5c9509d157692d1a18f90
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721446"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="2a2f6-101">EnvelopedCms varsayılan değer AES-256 şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="2a2f6-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="2a2f6-102">Tarafından kullanılan varsayılan simetrik şifreleme algoritması, `EnvelopedCms` TripleDES 'TEN AES-256 ' e değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="2a2f6-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2a2f6-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="2a2f6-103">Change description</span></span>

<span data-ttu-id="2a2f6-104">.NET Core Preview 7 ve önceki sürümlerinde, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> bir Oluşturucu aşırı yüklemesi aracılığıyla simetrik şifreleme algoritması belirtmeden verileri şifrelemek için kullanıldığında, veriler TripleDES/3DES/3DEA/DES3-engelleyebilecek algoritmayla şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="2a2f6-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="2a2f6-105">.NET Core 3,0 Preview 8 ' den itibaren ( [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet paketinin sürümü 4.6.0 aracılığıyla), varsayılan algoritma, algoritma modernleştirme için AES-256 olarak değiştirilmiştir ve varsayılan seçeneklerin güvenliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="2a2f6-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="2a2f6-106">Bir ileti alıcı sertifikasında (EC olmayan) bir Diffie-Hellman ortak anahtarı varsa, <xref:System.Security.Cryptography.CryptographicException> temel platformdaki sınırlamalar nedeniyle şifreleme işlemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a2f6-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="2a2f6-107">Aşağıdaki örnek kodda, veriler .NET Core 3,0 Preview 7 veya daha önceki sürümlerde çalışıyorsa üç aylık bir şekilde şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="2a2f6-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="2a2f6-108">.NET Core 3,0 Preview 8 veya üzeri sürümlerde çalışıyorsa, AES-256 ile şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="2a2f6-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="2a2f6-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2a2f6-109">Version introduced</span></span>

<span data-ttu-id="2a2f6-110">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="2a2f6-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a2f6-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2a2f6-111">Recommended action</span></span>

<span data-ttu-id="2a2f6-112">Değişiklik tarafından olumsuz bir şekilde etkilenmiyorsanız, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> Bu tür bir parametre içeren bir oluşturucuda, şifreleme algoritması tanımlayıcısını açıkça belirterek TripleDES şifrelemesini geri yükleyebilirsiniz <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> :</span><span class="sxs-lookup"><span data-stu-id="2a2f6-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="2a2f6-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="2a2f6-113">Category</span></span>

<span data-ttu-id="2a2f6-114">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="2a2f6-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a2f6-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2a2f6-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
