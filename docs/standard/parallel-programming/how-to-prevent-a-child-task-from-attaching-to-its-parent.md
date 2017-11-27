---
title: "Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4717e3a077648d9db51fe39228209617b384bd0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="f43cd-102">Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme</span><span class="sxs-lookup"><span data-stu-id="f43cd-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="f43cd-103">Bu belge, bir alt görevin üst göreve eklenmesini önleme gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f43cd-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="f43cd-104">Bir üçüncü taraf tarafından yazılmış ve görevleri de kullanan bir bileşen çağırdığınızda alt görevin üst göreve eklenmesini önleme yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="f43cd-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="f43cd-105">Örneğin, kullanan bir üçüncü taraf bileşen <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> oluşturmak için seçeneği bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesne sorunlara neden olabilir, kodunuzda uzun süre çalışan ise veya işlenmeyen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f43cd-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f43cd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f43cd-106">Example</span></span>  
 <span data-ttu-id="f43cd-107">Aşağıdaki örnek bir alt görevin üst göreve eklenmesini önleme etkileri için varsayılan seçenekleri kullanarak etkilerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="f43cd-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="f43cd-108">Örnekte bir <xref:System.Threading.Tasks.Task> de kullanan bir üçüncü taraf kitaplık içine çağıran nesne bir <xref:System.Threading.Tasks.Task> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f43cd-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="f43cd-109">Üçüncü taraf kitaplığını kullanan <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> oluşturmak için seçeneği <xref:System.Threading.Tasks.Task> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f43cd-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="f43cd-110">Uygulamanın kullandığı <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst görev oluşturmak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="f43cd-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="f43cd-111">Bu seçenek kaldırmak için çalışma zamanı bildirir <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> alt görevler belirtiminde.</span><span class="sxs-lookup"><span data-stu-id="f43cd-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="f43cd-112">Tüm alt görevler tamamlanana kadar üst göreve tamamlanmıyor olduğundan, uzun süre çalışan alt görevin kötü gerçekleştirmek genel uygulama neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f43cd-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="f43cd-113">Uygulama üst görevi oluşturmak için varsayılan seçenekleri kullandığında üst görev tamamlanmadan önce bu örnekte, alt görevin bitmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f43cd-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="f43cd-114">Uygulama kullandığında <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst, alt seçeneği bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="f43cd-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="f43cd-115">Bu nedenle, uygulama üst görev tamamlandıktan sonra ve alt görevin tamamlanmasını beklemeniz gerekir önce ek iş gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f43cd-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f43cd-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f43cd-116">Compiling the Code</span></span>  
 <span data-ttu-id="f43cd-117">Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DenyChildAttach.cs` (`DenyChildAttach.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f43cd-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="f43cd-118">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="f43cd-118">**csc.exe DenyChildAttach.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="f43cd-119">**Vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="f43cd-119">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f43cd-120">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f43cd-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43cd-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f43cd-121">See Also</span></span>  
 [<span data-ttu-id="f43cd-122">Görev tabanlı zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="f43cd-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
