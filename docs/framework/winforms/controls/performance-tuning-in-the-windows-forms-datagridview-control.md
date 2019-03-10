---
title: Windows Forms DataGridView Denetiminde Performans Ayarlaması
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: d425488adb8569a48333de4f8c0312143029fbe0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703182"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="dd3a8-102">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="dd3a8-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="dd3a8-103">Büyük miktarlarda verilerin çalışırken `DataGridView` dikkatle kullanmadığınız sürece, Denetim büyük miktarda bellek ek yüküne, kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="dd3a8-104">Sınırlı belleğe sahip istemciler üzerinde bu ek yükü bazıları maliyeti yüksek bir belleğe sahip özellikler önleyerek önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="dd3a8-105">Senaryonuz için bellek kullanımını özelleştirmek için sanal mod kullanarak kendiniz alma görevlerini ve bazılarını veya tümünü veri Bakımı de yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd3a8-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dd3a8-106">In This Section</span></span>  
 [<span data-ttu-id="dd3a8-107">Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dd3a8-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="dd3a8-108">Nasıl kullanılacağını açıklar `DataGridView` denetimi bir şekilde büyük miktarlarda veri ile çalışırken, gereksiz bellek kullanımını ve performansını yaptırımlara önler.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="dd3a8-109">Windows Forms DataGridView Denetiminde Sanal Mod</span><span class="sxs-lookup"><span data-stu-id="dd3a8-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="dd3a8-110">Standart veri bağlama mekanizması değiştirmek veya desteklemek için sanal mod kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="dd3a8-111">İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama</span><span class="sxs-lookup"><span data-stu-id="dd3a8-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="dd3a8-112">Birkaç sanal modu olayları için işleyiciler uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="dd3a8-113">Ayrıca, satır düzeyi geri alma ve kullanıcı düzenlemeleri için değişiklikleri uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="dd3a8-114">Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama</span><span class="sxs-lookup"><span data-stu-id="dd3a8-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="dd3a8-115">Kullanılabilir istemci bellek depolayabilirsiniz daha görüntülemek için daha fazla veriniz olduğunda, kullanışlı olan isteğe bağlı olarak veri yükleme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dd3a8-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="dd3a8-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="dd3a8-117">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="dd3a8-118">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3a8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd3a8-119">See also</span></span>
- [<span data-ttu-id="dd3a8-120">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="dd3a8-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="dd3a8-121">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="dd3a8-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
