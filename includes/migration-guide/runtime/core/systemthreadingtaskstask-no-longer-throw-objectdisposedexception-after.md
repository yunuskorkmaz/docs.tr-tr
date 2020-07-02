---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620592"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="5840b-101">System. Threading. Tasks. Task artık nesne atıldıktan sonra ObjectDisposedException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="5840b-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="5840b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5840b-102">Details</span></span>

<span data-ttu-id="5840b-103">Dışındaki <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> Yöntemler, <xref:System.Threading.Tasks.Task?displayProperty=fullName> <xref:System.ObjectDisposedException?displayProperty=fullName> nesne atıldıktan sonra artık özel durum oluşturmaz. Bu değişiklik önbelleğe alınan görevlerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="5840b-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="5840b-104">Örneğin, bir yöntem yeni bir görev ayırmak yerine zaten tamamlanmış bir işlemi temsil etmek için önbelleğe alınmış bir görevi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5840b-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="5840b-105">Herhangi bir görev kullanıcısı bunu atabildiğinden ve bu da onu kullanışsız hale getirdiğinden, bu önceki .NET Framework sürümlerinde mümkün değildi.</span><span class="sxs-lookup"><span data-stu-id="5840b-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5840b-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="5840b-106">Suggestion</span></span>

<span data-ttu-id="5840b-107">Görev yöntemlerinin <xref:System.ObjectDisposedException?displayProperty=fullName> , nesne atıldığı durumlarda artık oluşturamadığı farkında olun.</span><span class="sxs-lookup"><span data-stu-id="5840b-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="5840b-108">Bir uygulama, bir görevin atılmış olduğunu bildirmek üzere bu özel duruma bağlı ise, görevin durumunu açıkça denetlemek için güncelleştirilmeleri gerekir <xref:System.Threading.Tasks.Task.Status> .</span><span class="sxs-lookup"><span data-stu-id="5840b-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="5840b-109">Name</span><span class="sxs-lookup"><span data-stu-id="5840b-109">Name</span></span>    | <span data-ttu-id="5840b-110">Değer</span><span class="sxs-lookup"><span data-stu-id="5840b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5840b-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5840b-111">Scope</span></span>   |<span data-ttu-id="5840b-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="5840b-112">Minor</span></span>|
|<span data-ttu-id="5840b-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5840b-113">Version</span></span>|<span data-ttu-id="5840b-114">4,5</span><span class="sxs-lookup"><span data-stu-id="5840b-114">4.5</span></span>|
|<span data-ttu-id="5840b-115">Tür</span><span class="sxs-lookup"><span data-stu-id="5840b-115">Type</span></span>|<span data-ttu-id="5840b-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5840b-116">Runtime</span></span>|
