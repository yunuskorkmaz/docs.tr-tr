---
title: DataGridView denetiminde performans ayarlaması
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 77ad86c4cd606bcf074473c97371ec27bcc5605b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744267"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3c89b-102">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="3c89b-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3c89b-103">Büyük miktarda verilerle çalışırken, dikkatli bir şekilde kullanmadığınız müddetçe `DataGridView` denetimi ek yük olarak büyük miktarda bellek tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="3c89b-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="3c89b-104">Sınırlı belleğe sahip istemcilerde, yüksek bellek maliyeti olan özelliklerden kaçınarak bu ek yükün bazılarını önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c89b-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="3c89b-105">Senaryonuza yönelik bellek kullanımını özelleştirmek için, sanal modu kullanarak veri bakım ve alma görevlerinin bazılarını veya tümünü de yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c89b-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c89b-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3c89b-106">In This Section</span></span>  
 [<span data-ttu-id="3c89b-107">Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3c89b-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c89b-108">`DataGridView` denetiminin, büyük miktarlarda verilerle çalışırken gereksiz bellek kullanımını ve performans yaptırımlarını önleyen bir şekilde nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3c89b-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="3c89b-109">Windows Forms DataGridView Denetiminde Sanal Mod</span><span class="sxs-lookup"><span data-stu-id="3c89b-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c89b-110">Standart veri bağlama mekanizmasını tamamlamak veya değiştirmek için sanal modun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3c89b-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="3c89b-111">İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3c89b-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="3c89b-112">Birkaç sanal mod olay için işleyicilerin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3c89b-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="3c89b-113">Ayrıca, Kullanıcı düzenlemeleri için satır düzeyinde geri alma ve işlemeye nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c89b-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="3c89b-114">Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama</span><span class="sxs-lookup"><span data-stu-id="3c89b-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="3c89b-115">Kullanılabilir istemci belleğinin depolayabileceğinden daha fazla veriniz olduğunda yararlı olan verileri isteğe bağlı olarak nasıl yükleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="3c89b-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3c89b-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3c89b-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="3c89b-117"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c89b-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="3c89b-118"><xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c89b-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c89b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c89b-119">See also</span></span>

- [<span data-ttu-id="3c89b-120">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="3c89b-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="3c89b-121">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="3c89b-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
