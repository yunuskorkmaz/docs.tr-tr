---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614751"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a><span data-ttu-id="6ae06-101">OperationContext. Current, using yan tümcesinde çağrıldığında null döndürebilir</span><span class="sxs-lookup"><span data-stu-id="6ae06-101">OperationContext.Current may return null when called in a using clause</span></span>

#### <a name="details"></a><span data-ttu-id="6ae06-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6ae06-102">Details</span></span>

<span data-ttu-id="6ae06-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>`null` <xref:System.NullReferenceException> aşağıdaki koşulların tümü doğruysa dönebilir ve bir sonuç verebilir:</span><span class="sxs-lookup"><span data-stu-id="6ae06-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> may return `null` and a <xref:System.NullReferenceException> may result if all of the following conditions are true:</span></span>

- <span data-ttu-id="6ae06-104">Özelliğinin değerini, <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> veya döndüren bir yöntemde alırsınız <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="6ae06-104">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property in a method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="6ae06-105"><xref:System.ServiceModel.OperationContextScope>Bir `using` yan tümcede nesneyi örnekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae06-105">You instantiate the <xref:System.ServiceModel.OperationContextScope> object in a `using` clause.</span></span>
- <span data-ttu-id="6ae06-106">İçindeki özelliğinin değerini elde edersiniz <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> `using statement` .</span><span class="sxs-lookup"><span data-stu-id="6ae06-106">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property within the `using statement`.</span></span> <span data-ttu-id="6ae06-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ae06-107">For example:</span></span>

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a><span data-ttu-id="6ae06-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="6ae06-108">Suggestion</span></span>

<span data-ttu-id="6ae06-109">Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae06-109">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="6ae06-110">Yeni bir nesne olmayan yeni bir nesne örneği oluşturmak için kodunuzu aşağıdaki şekilde değiştirin `null` <xref:System.ServiceModel.OperationContext.Current%2A> :</span><span class="sxs-lookup"><span data-stu-id="6ae06-110">Modify your code as follows to instantiate a new non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> object:</span></span>

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- <span data-ttu-id="6ae06-111">En son güncelleştirmeyi .NET Framework 4.6.2 veya .NET Framework daha sonraki bir sürüme yükseltin.</span><span class="sxs-lookup"><span data-stu-id="6ae06-111">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="6ae06-112">Bu, içindeki akışını devre dışı <xref:System.Threading.ExecutionContext> bırakır <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> ve .NET Framework 4.6.1 ve ÖNCEKI sürümlerde WCF uygulamalarının davranışını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="6ae06-112">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> and restores the behavior of WCF applications in the .NET Framework 4.6.1 and earlier versions.</span></span> <span data-ttu-id="6ae06-113">Bu davranış yapılandırılabilir; yapılandırma dosyanıza aşağıdaki uygulama ayarı eklenerek eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="6ae06-113">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    <span data-ttu-id="6ae06-114">Bu değişiklik istenene ve uygulamanız, işlem bağlamları arasındaki yürütme bağlamına bağımlıysa, akışını şu şekilde etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ae06-114">If this change is undesirable and your application depends on execution context flowing between operation contexts, you can enable its flow as follows:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| <span data-ttu-id="6ae06-115">Name</span><span class="sxs-lookup"><span data-stu-id="6ae06-115">Name</span></span>    | <span data-ttu-id="6ae06-116">Değer</span><span class="sxs-lookup"><span data-stu-id="6ae06-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6ae06-117">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6ae06-117">Scope</span></span>   | <span data-ttu-id="6ae06-118">Edge</span><span class="sxs-lookup"><span data-stu-id="6ae06-118">Edge</span></span>        |
| <span data-ttu-id="6ae06-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6ae06-119">Version</span></span> | <span data-ttu-id="6ae06-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6ae06-120">4.6.2</span></span>       |
| <span data-ttu-id="6ae06-121">Tür</span><span class="sxs-lookup"><span data-stu-id="6ae06-121">Type</span></span>    | <span data-ttu-id="6ae06-122">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="6ae06-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6ae06-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6ae06-123">Affected APIs</span></span>

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
