---
ms.openlocfilehash: 1d2d6133683360b97569e49402e7c8c4d182b65d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235827"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="ea678-101">ObjectContext.Translate ve ObjectContext.ExecuteStoreQuery artık destek enum türü</span><span class="sxs-lookup"><span data-stu-id="ea678-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ea678-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ea678-102">Details</span></span>|<span data-ttu-id="ea678-103">.NET Framework 4.0, genel parametre <code>T</code> , <code>ObjectContext.Translate</code> ve <code>ObjectContext.ExecuteStoreQuery</code> yöntemleri bir sabit listesi yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="ea678-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="ea678-104">Bu senaryonun artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea678-104">That scenario is now supported.</span></span>|
|<span data-ttu-id="ea678-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="ea678-105">Suggestion</span></span>|<span data-ttu-id="ea678-106">Enum türü .NET Framework 4. 0'ı üzerinde Çevir veya ExecuteStoreQuery çağrıldı, '0' döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ea678-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="ea678-107">Bu davranışı arzu olduysa, çağrıları 0 sabiti (veya onu enum eşdeğeri) ile değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ea678-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>|
|<span data-ttu-id="ea678-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ea678-108">Scope</span></span>|<span data-ttu-id="ea678-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="ea678-109">Edge</span></span>|
|<span data-ttu-id="ea678-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ea678-110">Version</span></span>|<span data-ttu-id="ea678-111">4,5</span><span class="sxs-lookup"><span data-stu-id="ea678-111">4.5</span></span>|
|<span data-ttu-id="ea678-112">Tür</span><span class="sxs-lookup"><span data-stu-id="ea678-112">Type</span></span>|<span data-ttu-id="ea678-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ea678-113">Runtime</span></span>|
|<span data-ttu-id="ea678-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ea678-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
