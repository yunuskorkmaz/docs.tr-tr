---
ms.openlocfilehash: bc33266bb2af639d7d0d1cb532ed73abd7f1ba9a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803233"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="85434-101">EF QueryViews için belirli özelliklere sahip artık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85434-101">EF no longer throws for QueryViews with specific characteristics</span></span>

|   |   |
|---|---|
|<span data-ttu-id="85434-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="85434-102">Details</span></span>|<span data-ttu-id="85434-103">Entity Framework artık oluşturur bir <xref:System.StackOverflowException?displayProperty=name> uygulama ile bir 0..1 bir QueryView içeren bir sorgu yürütüldüğünde bir özel durum sorgunun bir parçası ilişkili varlıkları içermesi dener gezinme özelliği.</span><span class="sxs-lookup"><span data-stu-id="85434-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=name> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="85434-104">Örneğin, arama tarafından <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span><span class="sxs-lookup"><span data-stu-id="85434-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>|
|<span data-ttu-id="85434-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="85434-105">Suggestion</span></span>|<span data-ttu-id="85434-106">Bu değişiklik, yalnızca 1 ile QueryViews kullanan kodu etkiler-0..1 çalışan bu çağrı sorguladığında ilişkileri. İçerir.</span><span class="sxs-lookup"><span data-stu-id="85434-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="85434-107">Güvenilirlik artar ve neredeyse tüm uygulamalar için saydam olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85434-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="85434-108">Beklenmeyen davranışlara neden olur, ancak bu aşağıdaki girişe ekleyerek devre dışı bırakabilirsiniz <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="85434-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="85434-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="85434-109">Scope</span></span>|<span data-ttu-id="85434-110">Kenar</span><span class="sxs-lookup"><span data-stu-id="85434-110">Edge</span></span>|
|<span data-ttu-id="85434-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="85434-111">Version</span></span>|<span data-ttu-id="85434-112">4.5.2</span><span class="sxs-lookup"><span data-stu-id="85434-112">4.5.2</span></span>|
|<span data-ttu-id="85434-113">Tür</span><span class="sxs-lookup"><span data-stu-id="85434-113">Type</span></span>|<span data-ttu-id="85434-114">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="85434-114">Runtime</span></span>|

