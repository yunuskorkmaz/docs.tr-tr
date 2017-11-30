---
title: "Windows Forms DataGridView Denetiminde Performans Ayarlaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452c55d38a896ec96e0992a4b9826f08dc4caa0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4dec4-102">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="4dec4-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4dec4-103">Büyük miktarlarda verilerin çalışırken `DataGridView` dikkatle kullanmadığınız sürece denetim çok miktarda ek yük, bellekte tüketebileceği.</span><span class="sxs-lookup"><span data-stu-id="4dec4-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="4dec4-104">Sınırlı belleği olan istemciler üzerinde bu ek yükü bazıları maliyeti yüksek bellek sahip özellikleri kaçınarak önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dec4-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="4dec4-105">Senaryonuz için bellek kullanımını özelleştirmek için sanal modu kullanarak kendiniz alma görevleri ve bazılarını veya tümünü veri bakımı da yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dec4-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4dec4-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4dec4-106">In This Section</span></span>  
 [<span data-ttu-id="4dec4-107">Windows Forms DataGridView denetimini ölçeklendirme için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="4dec4-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4dec4-108">Nasıl kullanılacağını açıklar `DataGridView` , büyük miktarlarda veri çalışırken gereksiz bellek kullanımı ve performans cezaları önler şekilde denetim.</span><span class="sxs-lookup"><span data-stu-id="4dec4-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="4dec4-109">Sanal mod Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="4dec4-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4dec4-110">Sanal mod tamamlayabilir veya standart veri bağlama mekanizması değiştirmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4dec4-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="4dec4-111">İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama</span><span class="sxs-lookup"><span data-stu-id="4dec4-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="4dec4-112">Birden fazla sanal modu olayları için işleyiciler uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="4dec4-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="4dec4-113">Ayrıca satır düzeyi geri alma ve kullanıcı düzenlemeleri için yürütme uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="4dec4-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="4dec4-114">Tam zamanında veri Windows Forms DataGridView denetiminde yükleme ile sanal modu uygulama</span><span class="sxs-lookup"><span data-stu-id="4dec4-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="4dec4-115">Kullanılabilir istemci bellek depolayabilir daha görüntülemek için daha fazla veri varsa, yararlı olan isteğe bağlı veri yükleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="4dec4-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4dec4-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="4dec4-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="4dec4-117">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="4dec4-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="4dec4-118">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4dec4-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dec4-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4dec4-119">See Also</span></span>  
 [<span data-ttu-id="4dec4-120">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="4dec4-120">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="4dec4-121">Windows Forms DataGridView denetiminde veri görüntüleme modları</span><span class="sxs-lookup"><span data-stu-id="4dec4-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
