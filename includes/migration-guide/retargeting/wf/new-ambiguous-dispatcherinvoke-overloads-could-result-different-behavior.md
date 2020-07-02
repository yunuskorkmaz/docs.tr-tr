---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617262"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="9d622-101">Yeni (belirsiz) dağıtıcı. aşırı yüklemeleri çağır farklı davranışa neden olabilir</span><span class="sxs-lookup"><span data-stu-id="9d622-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="9d622-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9d622-102">Details</span></span>

<span data-ttu-id="9d622-103">.NET Framework 4,5, öğesine bir parametre içeren yeni aşırı yüklemeler ekler <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> <xref:System.Action> .</span><span class="sxs-lookup"><span data-stu-id="9d622-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="9d622-104">Mevcut kod yeniden derlendiğinde, derleyiciler, Dispatcher çağrılarını çözümleyebilir. Invoke metotları için bir parametre içeren bir parametresi olan bir parametreye sahip metotları çağırır. <xref:System.Delegate> <xref:System.Action></span><span class="sxs-lookup"><span data-stu-id="9d622-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="9d622-105">Bir Dispatcher çağrısı olarak, bir dağıtıcı çağrısı olarak bir parametre ile aşırı yüklemeyi çağır. bir <xref:System.Delegate> parametre ile aşırı yüklemeyi çağırma <xref:System.Action> , davranış ile ilgili aşağıdaki farklılıklar oluşabilir</span><span class="sxs-lookup"><span data-stu-id="9d622-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="9d622-106">Bir özel durum oluşursa, <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> ve <xref:System.Windows.Threading.Dispatcher.UnhandledException> olayları oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="9d622-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="9d622-107">Bunun yerine, özel durumlar olay tarafından işlenir <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="9d622-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="9d622-108">, Gibi bazı üyelere yapılan çağrılar, <xref:System.Windows.Threading.DispatcherOperation.Result> işlem tamamlanana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="9d622-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9d622-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="9d622-109">Suggestion</span></span>

<span data-ttu-id="9d622-110">Belirsizlik (ve özel durum işleme veya engelleme davranışındaki olası farklılıklar) önlemek için, Dispatcher. Invoke çağrısı, .NET Framework 4,0 yöntem aşırı yüklemesine çözümlendiğinizden emin olmak için çağırma çağrısına ikinci parametre olarak boş bir [] nesnesi geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="9d622-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="9d622-111">Name</span><span class="sxs-lookup"><span data-stu-id="9d622-111">Name</span></span>    | <span data-ttu-id="9d622-112">Değer</span><span class="sxs-lookup"><span data-stu-id="9d622-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9d622-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9d622-113">Scope</span></span>   | <span data-ttu-id="9d622-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="9d622-114">Minor</span></span>       |
| <span data-ttu-id="9d622-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9d622-115">Version</span></span> | <span data-ttu-id="9d622-116">4,5</span><span class="sxs-lookup"><span data-stu-id="9d622-116">4.5</span></span>         |
| <span data-ttu-id="9d622-117">Tür</span><span class="sxs-lookup"><span data-stu-id="9d622-117">Type</span></span>    | <span data-ttu-id="9d622-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="9d622-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="9d622-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9d622-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
