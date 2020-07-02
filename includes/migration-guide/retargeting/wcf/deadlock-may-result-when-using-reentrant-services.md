---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614786"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="ca423-101">Yer elde edilen hizmetler kullanılırken kilitlenme oluşabilir</span><span class="sxs-lookup"><span data-stu-id="ca423-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="ca423-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ca423-102">Details</span></span>

<span data-ttu-id="ca423-103">Bir kilitlenme, hizmet örneklerini aynı anda bir yürütme iş parçacığına kısıtlayan bir tekrar hizmet ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ca423-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="ca423-104">Bu sorunla karşılaşacağınız hizmetler, kodunda aşağıdaki gibi olacaktır <xref:System.ServiceModel.ServiceBehaviorAttribute> :</span><span class="sxs-lookup"><span data-stu-id="ca423-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="ca423-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="ca423-105">Suggestion</span></span>

<span data-ttu-id="ca423-106">Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ca423-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="ca423-107">Hizmetin eşzamanlılık modunu <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> veya &lt; System. ServiceModel. ConcurrencyMode. Multiple? DisplayProperty = nameWithType olarak ayarlayın &gt; .</span><span class="sxs-lookup"><span data-stu-id="ca423-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span></span> <span data-ttu-id="ca423-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ca423-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="ca423-109">En son güncelleştirmeyi .NET Framework 4.6.2 veya .NET Framework daha sonraki bir sürüme yükseltin.</span><span class="sxs-lookup"><span data-stu-id="ca423-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="ca423-110">Bu, içindeki akışını devre dışı <xref:System.Threading.ExecutionContext> bırakır <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ca423-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ca423-111">Bu davranış yapılandırılabilir; yapılandırma dosyanıza aşağıdaki uygulama ayarı eklenerek eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="ca423-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="ca423-112">Değeri, tekrar eden `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` Hizmetler için hiçbir şekilde ayarlanmamalıdır `false` .</span><span class="sxs-lookup"><span data-stu-id="ca423-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="ca423-113">Name</span><span class="sxs-lookup"><span data-stu-id="ca423-113">Name</span></span>    | <span data-ttu-id="ca423-114">Değer</span><span class="sxs-lookup"><span data-stu-id="ca423-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca423-115">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ca423-115">Scope</span></span>   | <span data-ttu-id="ca423-116">İkincil</span><span class="sxs-lookup"><span data-stu-id="ca423-116">Minor</span></span>       |
| <span data-ttu-id="ca423-117">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ca423-117">Version</span></span> | <span data-ttu-id="ca423-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ca423-118">4.6.2</span></span>       |
| <span data-ttu-id="ca423-119">Tür</span><span class="sxs-lookup"><span data-stu-id="ca423-119">Type</span></span>    | <span data-ttu-id="ca423-120">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="ca423-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ca423-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ca423-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
