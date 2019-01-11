---
title: 'Nasıl yapılır: Bir alt görevin kendi üst öğesine eklenmesini önleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7506a57e29b7942bd06141baa2d2b048ed998214
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221537"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="d565c-102">Nasıl yapılır: Bir alt görevin kendi üst öğesine eklenmesini önleme</span><span class="sxs-lookup"><span data-stu-id="d565c-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="d565c-103">Bu belge, bir alt görevin üst göreve eklenmesini önleme gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d565c-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="d565c-104">Bir üçüncü taraf tarafından yazılan ve görevleri de kullanan bir bileşen çağırdığınızda, bir alt görevin üst göreve eklenmesini önleme yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d565c-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="d565c-105">Örneğin, kullanan bir üçüncü parti bileşeniniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> oluşturma seçeneği bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesne sorunlara neden olabilir, kodunuzda uzun süreli veya işlenmeyen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d565c-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d565c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d565c-106">Example</span></span>  
 <span data-ttu-id="d565c-107">Aşağıdaki örnek, bir alt görevin üst göreve eklenmesini önleme etkileri için varsayılan seçenekleri kullanarak etkilerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="d565c-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="d565c-108">Örnek bir <xref:System.Threading.Tasks.Task> de kullanan bir üçüncü taraf kitaplığına çağıran bir nesne bir <xref:System.Threading.Tasks.Task> nesne.</span><span class="sxs-lookup"><span data-stu-id="d565c-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="d565c-109">Üçüncü taraf kitaplığı kullandığını <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> oluşturma seçeneği <xref:System.Threading.Tasks.Task> nesne.</span><span class="sxs-lookup"><span data-stu-id="d565c-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="d565c-110">Uygulamanın kullandığı <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst görev oluşturma seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d565c-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="d565c-111">Bu seçeneği kaldırmak için çalışma zamanı bildirir <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> alt görevlerdeki belirtimi.</span><span class="sxs-lookup"><span data-stu-id="d565c-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="d565c-112">Tüm alt görevler tamamlanıncaya kadar bir üst görev sonlanmaz, uzun süre çalışan alt görev genel uygulamanın sonlanmayacağından neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d565c-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="d565c-113">Uygulama, üst görev oluşturmak için varsayılan seçenekleri kullandığında bu örnekte, alt görev üst görev tamamlanmadan önce tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d565c-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="d565c-114">Uygulama kullandığında <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneği, alt üst öğeye bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="d565c-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="d565c-115">Bu nedenle, uygulamanın ek iş üst görev tamamlandıktan sonra ve son alt görevin tamamlanmasını beklemelisiniz önce gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d565c-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d565c-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d565c-116">Compiling the Code</span></span>  
 <span data-ttu-id="d565c-117">Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `DenyChildAttach.cs` (`DenyChildAttach.vb` Visual Basic için), ve ardından Geliştirici komut istemi penceresi Visual Studio için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d565c-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for Visual Basic), and then run the following command in a Developer Command Prompt for Visual Studio window.</span></span>  
  
 <span data-ttu-id="d565c-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="d565c-118">Visual C#</span></span>  
  
 <span data-ttu-id="d565c-119">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="d565c-119">**csc.exe DenyChildAttach.cs**</span></span>  
  
 <span data-ttu-id="d565c-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d565c-120">Visual Basic</span></span>  
  
 <span data-ttu-id="d565c-121">**Vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="d565c-121">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d565c-122">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d565c-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d565c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d565c-123">See also</span></span>

- [<span data-ttu-id="d565c-124">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="d565c-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
