---
title: "Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1c11ca487003e57a499b3ff46178350e6aad404
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c0ab8-102">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="c0ab8-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c0ab8-103">`DataGridView` Denetim satırları ve sütunları boyutlandırma davranışını özelleştirmek için çeşitli seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="c0ab8-104">Genellikle, `DataGridView` hücrelerle değil yeniden boyutlandırmak bunların içeriğine göre.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="c0ab8-105">Bunun yerine, hücreden daha büyük bir görüntüleme değeri küçük.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="c0ab8-106">İçerik dize olarak görüntülenebilir, hücre bir araç ipucunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="c0ab8-107">Varsayılan olarak, kullanıcılar satır, sütun ve üstbilgi Bölücü daha fazla bilgi göstermek için fareyle sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="c0ab8-108">Kullanıcılar ayrıca otomatik olarak bu içeriklere dayalı ilişkili satır, sütun veya üstbilgi bant yeniden boyutlandırmak için ayırıcı çift tıklatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="c0ab8-109">`DataGridView` Denetimi özellikleri, yöntemleri ve özelleştirebilir veya bu kullanıcıyı yönlendiren davranışları tümünün devre dışı bırakmak etkinleştirmeniz olayları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="c0ab8-110">Ayrıca, satırlar, sütunlar ve bunların içeriklerin sığması için üstbilgiler program aracılığıyla boyutlandırabilirsiniz veya bunları içeriklerini değiştirdiğinizde otomatik olarak kendilerini yeniden boyutlandırmak için yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="c0ab8-111">Sütunları otomatik olarak belirttiğiniz oranları denetiminde kullanılabilir genişliğini bölmek için de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0ab8-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c0ab8-112">In This Section</span></span>  
 [<span data-ttu-id="c0ab8-113">Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c0ab8-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c0ab8-114">Boyutlandırma satırlar, sütunlar ve üst bilgileri için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="c0ab8-115">Ayrıca boyutlandırma ile ilgili özellikleri ve yöntemleri hakkında ayrıntılar sağlar ve genel kullanım senaryoları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="c0ab8-116">Windows Forms DataGridView Denetiminde Sütun Doldurma Modu</span><span class="sxs-lookup"><span data-stu-id="c0ab8-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c0ab8-117">Sütun doldurma modu ayrıntılı açıklar ve sütun doldurma modu ve Diğer modları denemek için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="c0ab8-118">Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c0ab8-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c0ab8-119">Boyutlandırma modlarını genel amaçlar için yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="c0ab8-120">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçeriği Sığdıracak Şekilde Hücreleri Programlı Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="c0ab8-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="c0ab8-121">Program yeniden boyutlandırma ile denemek için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="c0ab8-122">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçerik Değiştiğinde Hücreleri Otomatik Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="c0ab8-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="c0ab8-123">Otomatik boyutlandırma modlarıyla denemeler için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c0ab8-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c0ab8-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c0ab8-125">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ab8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0ab8-126">See Also</span></span>  
 [<span data-ttu-id="c0ab8-127">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="c0ab8-127">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
