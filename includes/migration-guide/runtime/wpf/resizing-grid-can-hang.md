---
ms.openlocfilehash: 8dc1b4d94d01813a8124d1340b50fa78a9b157f8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496815"
---
### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="47e40-101">Bir kılavuzun yeniden boyutlandırılması askıda kalabilir</span><span class="sxs-lookup"><span data-stu-id="47e40-101">Resizing a Grid can hang</span></span>

#### <a name="details"></a><span data-ttu-id="47e40-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="47e40-102">Details</span></span>

<span data-ttu-id="47e40-103">Aşağıdaki koşullarda bir öğesinin düzeni sırasında sonsuz bir döngü meydana gelebilir <code>T:System.Windows.Controls.Grid</code> :</span><span class="sxs-lookup"><span data-stu-id="47e40-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="47e40-104">Satır tanımları \* , hem MinHeight hem de MaxHeight bildiren iki satır içerir.</span><span class="sxs-lookup"><span data-stu-id="47e40-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="47e40-105">\*-Satırların içeriği karşılık gelen MaxHeight değerini aşamaz</span><span class="sxs-lookup"><span data-stu-id="47e40-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="47e40-106">Kılavuzun kullanılabilir yüksekliği ilk MinHeight (artı diğer tüm sabit veya otomatik satırlar) ile aşıldı</span><span class="sxs-lookup"><span data-stu-id="47e40-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="47e40-107">Uygulama, 4,7 .NET Framework veya ayarlarını yaparak 4,7 ayırma algoritmasında <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span><span class="sxs-lookup"><span data-stu-id="47e40-107">The app targets .NET Framework 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="47e40-108">Döngü aynı zamanda ikiden fazla satır veya sütun için büyük/küçük harf ile de gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="47e40-108">The loop would also happen with more than two rows, or in the analogous case for columns.</span></span> <span data-ttu-id="47e40-109">Sorun .NET Framework 4.7.1 içinde düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="47e40-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="47e40-110">Öneri</span><span class="sxs-lookup"><span data-stu-id="47e40-110">Suggestion</span></span>

<span data-ttu-id="47e40-111">.NET Framework 4.7.1 ' ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="47e40-111">Upgrade to .NET Framework 4.7.1.</span></span>  <span data-ttu-id="47e40-112">Alternatif olarak, 4,7 ayırma algoritmasına ihtiyacınız yoksa aşağıdaki yapılandırma ayarını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="47e40-112">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="47e40-113">Name</span><span class="sxs-lookup"><span data-stu-id="47e40-113">Name</span></span>    | <span data-ttu-id="47e40-114">Değer</span><span class="sxs-lookup"><span data-stu-id="47e40-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="47e40-115">Kapsam</span><span class="sxs-lookup"><span data-stu-id="47e40-115">Scope</span></span>   |<span data-ttu-id="47e40-116">Edge</span><span class="sxs-lookup"><span data-stu-id="47e40-116">Edge</span></span>|
|<span data-ttu-id="47e40-117">Sürüm</span><span class="sxs-lookup"><span data-stu-id="47e40-117">Version</span></span>|<span data-ttu-id="47e40-118">4,7</span><span class="sxs-lookup"><span data-stu-id="47e40-118">4.7</span></span>|
|<span data-ttu-id="47e40-119">Tür</span><span class="sxs-lookup"><span data-stu-id="47e40-119">Type</span></span>|<span data-ttu-id="47e40-120">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="47e40-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="47e40-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="47e40-121">Affected APIs</span></span>

<span data-ttu-id="47e40-122">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="47e40-122">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
