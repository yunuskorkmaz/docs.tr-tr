---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620627"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="61e43-101">EF artık belirli özelliklere sahip QueryViews için oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="61e43-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="61e43-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="61e43-102">Details</span></span>

<span data-ttu-id="61e43-103">Entity Framework, bir uygulama bir <xref:System.StackOverflowException?displayProperty=fullName> QueryView içeren bir sorgu yürüttüğünde, ilişkili varlıkları sorgunun bir parçası olarak içerme girişiminde bulunan 0.. 1 gezinti özelliği içeren bir sorgu çalıştırdığında artık bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="61e43-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="61e43-104">Örneğin, çağırarak <code>.Include(e =&gt; e.RelatedNavProp)</code> .</span><span class="sxs-lookup"><span data-stu-id="61e43-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="61e43-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="61e43-105">Suggestion</span></span>

<span data-ttu-id="61e43-106">Bu değişiklik yalnızca, çağıran sorguları çalıştırırken 1-0.. 1 ilişkiyle birlikte QueryViews kullanan kodu etkiler. İçeriyor.</span><span class="sxs-lookup"><span data-stu-id="61e43-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="61e43-107">Güvenilirliği artırır ve neredeyse tüm uygulamalara şeffaf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="61e43-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="61e43-108">Ancak, beklenmeyen davranışlara neden oluyorsa, <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasının bölümüne aşağıdaki girdiyi ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="61e43-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="61e43-109">Name</span><span class="sxs-lookup"><span data-stu-id="61e43-109">Name</span></span>    | <span data-ttu-id="61e43-110">Değer</span><span class="sxs-lookup"><span data-stu-id="61e43-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="61e43-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="61e43-111">Scope</span></span>   |<span data-ttu-id="61e43-112">Edge</span><span class="sxs-lookup"><span data-stu-id="61e43-112">Edge</span></span>|
|<span data-ttu-id="61e43-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="61e43-113">Version</span></span>|<span data-ttu-id="61e43-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="61e43-114">4.5.2</span></span>|
|<span data-ttu-id="61e43-115">Tür</span><span class="sxs-lookup"><span data-stu-id="61e43-115">Type</span></span>|<span data-ttu-id="61e43-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="61e43-116">Runtime</span></span>|
