---
ms.openlocfilehash: acb8ed44b7d18b257731e32339f087c8fe5fdd4a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721696"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="e7b7d-101">Microsoft. VisualBasic. MyServices ad alanındaki türler kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="e7b7d-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="e7b7d-102"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>Ad alanındaki türler kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e7b7d-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7b7d-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e7b7d-103">Version introduced</span></span>

<span data-ttu-id="e7b7d-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e7b7d-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="e7b7d-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e7b7d-105">Change description</span></span>

<span data-ttu-id="e7b7d-106">Ad alanındaki türler, <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e7b7d-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="e7b7d-107">.NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="e7b7d-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="e7b7d-108">Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7b7d-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7b7d-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e7b7d-109">Recommended action</span></span>

<span data-ttu-id="e7b7d-110">Kodunuz **Microsoft. VisualBasic. MyServices** türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen türler ve Üyeler vardır.</span><span class="sxs-lookup"><span data-stu-id="e7b7d-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="e7b7d-111">Aşağıda, **Microsoft. VisualBasic. MyServices** türlerinin eşdeğer .NET sınıf kitaplığı türlerine eşlenmesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e7b7d-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="e7b7d-112">Microsoft. VisualBasic. MyServices türü</span><span class="sxs-lookup"><span data-stu-id="e7b7d-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="e7b7d-113">.NET sınıf kitaplığı türü</span><span class="sxs-lookup"><span data-stu-id="e7b7d-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="e7b7d-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>WPF uygulamaları için <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> Windows Forms uygulamalar için</span><span class="sxs-lookup"><span data-stu-id="e7b7d-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="e7b7d-115"><xref:System.IO>Ad alanındaki türler</span><span class="sxs-lookup"><span data-stu-id="e7b7d-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="e7b7d-116">Ad alanındaki kayıt defteri ile ilgili türler <xref:Microsoft.Win32></span><span class="sxs-lookup"><span data-stu-id="e7b7d-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="e7b7d-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="e7b7d-117">Category</span></span>

<span data-ttu-id="e7b7d-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7b7d-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7b7d-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e7b7d-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
