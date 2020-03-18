---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116331"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="f7c5d-101">Microsoft.VisualBasic.MyServices ad alanında türleri kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="f7c5d-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="f7c5d-102"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> Ad alanındaki türler kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f7c5d-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f7c5d-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f7c5d-103">Version introduced</span></span>

<span data-ttu-id="f7c5d-104">.NET Core 3.0 Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="f7c5d-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="f7c5d-105">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="f7c5d-105">Change description</span></span>

<span data-ttu-id="f7c5d-106"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> Ad alanındaki türler bazı .NET Core 3.0 Önizleme sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7c5d-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="f7c5d-107">.NET Core 3.0 Preview 9 ile başlayarak artık kullanılamazlar.</span><span class="sxs-lookup"><span data-stu-id="f7c5d-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="f7c5d-108">Türler, gereksiz derleme bağımlılıklarını veya sonraki sürümlerde değişiklikleri kırmayı önlemek için kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="f7c5d-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f7c5d-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f7c5d-109">Recommended action</span></span>

<span data-ttu-id="f7c5d-110">Kodunuz **Microsoft.VisualBasic.MyServices** türlerinin ve üyelerinin kullanımına bağlıysa, .NET sınıf kitaplığında karşılık gelen türler ve üyeler vardır.</span><span class="sxs-lookup"><span data-stu-id="f7c5d-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="f7c5d-111">Aşağıda, **Microsoft.VisualBasic.MyServices** türlerinin eşdeğer .NET sınıf kitaplık türlerine göre eşlemeleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f7c5d-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="f7c5d-112">Microsoft.VisualBasic.MyServices türü</span><span class="sxs-lookup"><span data-stu-id="f7c5d-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="f7c5d-113">.NET sınıf kitaplık türü</span><span class="sxs-lookup"><span data-stu-id="f7c5d-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="f7c5d-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>WPF uygulamaları için, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> Windows Forms uygulamaları için</span><span class="sxs-lookup"><span data-stu-id="f7c5d-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="f7c5d-115"><xref:System.IO> Ad alanındaki türleri</span><span class="sxs-lookup"><span data-stu-id="f7c5d-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="f7c5d-116"><xref:Microsoft.Win32> Ad alanında kayıt defteri yle ilgili türler</span><span class="sxs-lookup"><span data-stu-id="f7c5d-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="f7c5d-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="f7c5d-117">Category</span></span>

<span data-ttu-id="f7c5d-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f7c5d-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7c5d-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f7c5d-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
