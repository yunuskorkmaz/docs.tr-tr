---
ms.openlocfilehash: 7766a59131fffe2b436c15a5ff58e67001be7941
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065115"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a><span data-ttu-id="96b8d-101">CryptoStream. Dispose, son bloğu yalnızca yazma sırasında dönüştürür</span><span class="sxs-lookup"><span data-stu-id="96b8d-101">CryptoStream.Dispose transforms final block only when writing</span></span>

<span data-ttu-id="96b8d-102"><xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType>İşlemleri tamamlaması için kullanılan yöntemi, `CryptoStream` okurken artık son bloğu dönüştürmeyi denemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="96b8d-102">The <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> method, which is used to finish `CryptoStream` operations, no longer attempts to transform the final block when reading.</span></span>

#### <a name="change-description"></a><span data-ttu-id="96b8d-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="96b8d-103">Change description</span></span>

<span data-ttu-id="96b8d-104">Önceki .NET sürümlerinde, bir kullanıcı modunda kullanırken tamamlanmamış bir okuma gerçekleştirdiyse <xref:System.Security.Cryptography.CryptoStream> <xref:System.Security.Cryptography.CryptoStreamMode.Read> , <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> Yöntem bir özel durum oluşturabilir (örneğin, doldurma ile AES kullanırken).</span><span class="sxs-lookup"><span data-stu-id="96b8d-104">In previous .NET versions, if a user performed an incomplete read when using <xref:System.Security.Cryptography.CryptoStream> in <xref:System.Security.Cryptography.CryptoStreamMode.Read> mode, the <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> method could throw an exception (for example, when using AES with padding).</span></span> <span data-ttu-id="96b8d-105">Son blok dönüştürülürken, ancak veriler eksik olduğundan özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="96b8d-105">The exception was thrown because the final block was attempted to be transformed but the data was incomplete.</span></span>

<span data-ttu-id="96b8d-106">.NET Core 3,0 ve sonraki sürümlerinde, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> artık okuma sırasında son bloğu dönüştürmeyi denemeyecek ve bu da tamamlanmamış okumaların yapılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="96b8d-106">In .NET Core 3.0 and later versions, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> no longer tries to transform the final block when reading, which allows for incomplete reads.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="96b8d-107">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="96b8d-107">Reason for change</span></span>

<span data-ttu-id="96b8d-108">Bu değişiklik, bir özel durum yakalamak zorunda kalmadan bir ağ işlemi iptal edildiğinde şifre akışından tamamlanmamış okuma işlemleri yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="96b8d-108">This change enables incomplete reads from the crypto stream when a network operation is cancelled, without the need to catch an exception.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="96b8d-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="96b8d-109">Version introduced</span></span>

<span data-ttu-id="96b8d-110">3.0</span><span class="sxs-lookup"><span data-stu-id="96b8d-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="96b8d-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="96b8d-111">Recommended action</span></span>

<span data-ttu-id="96b8d-112">Çoğu uygulama bu değişiklikten etkilenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="96b8d-112">Most apps should not be affected by this change.</span></span>

<span data-ttu-id="96b8d-113">Uygulamanız tamamlanmamış bir okuma durumunda daha önce bir özel durum yakalandığında, bu `catch` bloğu silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96b8d-113">If your application previously caught an exception in case of an incomplete read, you can delete that `catch` block.</span></span>
<span data-ttu-id="96b8d-114">Uygulamanız, karma senaryolarda son bloğunun dönüştürülmesini kullanıyorsa, tüm akışın atılmadan önce okunduğunuzdan emin olmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="96b8d-114">If your app used transforming of the final block in hashing scenarios, you might need to ensure that the entire stream is read before it's disposed.</span></span>

#### <a name="category"></a><span data-ttu-id="96b8d-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="96b8d-115">Category</span></span>

<span data-ttu-id="96b8d-116">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="96b8d-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="96b8d-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="96b8d-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->
