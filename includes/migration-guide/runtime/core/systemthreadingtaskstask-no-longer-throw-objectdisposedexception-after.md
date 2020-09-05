---
ms.openlocfilehash: 58dbb54d42d89b450134758072e3133ae4e6b13d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496401"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="3e2d4-101">System. Threading. Tasks. Task artık nesne atıldıktan sonra ObjectDisposedException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="3e2d4-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="3e2d4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3e2d4-102">Details</span></span>

<span data-ttu-id="3e2d4-103">Dışındaki <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> Yöntemler, <xref:System.Threading.Tasks.Task?displayProperty=fullName> <xref:System.ObjectDisposedException?displayProperty=fullName> nesne atıldıktan sonra artık özel durum oluşturmaz. Bu değişiklik önbelleğe alınan görevlerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="3e2d4-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="3e2d4-104">Örneğin, bir yöntem yeni bir görev ayırmak yerine zaten tamamlanmış bir işlemi temsil etmek için önbelleğe alınmış bir görevi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3e2d4-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="3e2d4-105">Herhangi bir görev kullanıcısı bunu atabildiğinden ve bu da onu kullanışsız hale getirdiğinden, bu önceki .NET Framework sürümlerinde mümkün değildi.</span><span class="sxs-lookup"><span data-stu-id="3e2d4-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3e2d4-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="3e2d4-106">Suggestion</span></span>

<span data-ttu-id="3e2d4-107">Görev yöntemlerinin <xref:System.ObjectDisposedException?displayProperty=fullName> , nesne atıldığı durumlarda artık oluşturamadığı farkında olun.</span><span class="sxs-lookup"><span data-stu-id="3e2d4-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="3e2d4-108">Bir uygulama, bir görevin atılmış olduğunu bildirmek üzere bu özel duruma bağlı ise, görevin durumunu açıkça denetlemek için güncelleştirilmeleri gerekir <xref:System.Threading.Tasks.Task.Status> .</span><span class="sxs-lookup"><span data-stu-id="3e2d4-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="3e2d4-109">Name</span><span class="sxs-lookup"><span data-stu-id="3e2d4-109">Name</span></span>    | <span data-ttu-id="3e2d4-110">Değer</span><span class="sxs-lookup"><span data-stu-id="3e2d4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3e2d4-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3e2d4-111">Scope</span></span>   |<span data-ttu-id="3e2d4-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="3e2d4-112">Minor</span></span>|
|<span data-ttu-id="3e2d4-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3e2d4-113">Version</span></span>|<span data-ttu-id="3e2d4-114">4,5</span><span class="sxs-lookup"><span data-stu-id="3e2d4-114">4.5</span></span>|
|<span data-ttu-id="3e2d4-115">Tür</span><span class="sxs-lookup"><span data-stu-id="3e2d4-115">Type</span></span>|<span data-ttu-id="3e2d4-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="3e2d4-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3e2d4-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3e2d4-117">Affected APIs</span></span>

<span data-ttu-id="3e2d4-118">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="3e2d4-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
