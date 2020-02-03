---
title: DataGridView Denetimindeki sütunları ve satırları yeniden boyutlandırma
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742417"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="820fc-102">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="820fc-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="820fc-103">`DataGridView` denetimi, sütunlarının ve satırlarının boyutlandırma davranışını özelleştirmek için çok sayıda seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="820fc-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="820fc-104">Genellikle, `DataGridView` hücreleri içeriklerine göre yeniden boyutlandırmaz.</span><span class="sxs-lookup"><span data-stu-id="820fc-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="820fc-105">Bunun yerine, hücreden daha büyük olan herhangi bir görüntüleme değerini kırpırlar.</span><span class="sxs-lookup"><span data-stu-id="820fc-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="820fc-106">İçerik bir dize olarak görüntülenebiliyorsanız, hücre onu bir araç Ipucunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="820fc-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="820fc-107">Kullanıcılar, varsayılan olarak satır, sütun ve başlık bölücüleri fareyle sürükleyerek daha fazla bilgi görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="820fc-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="820fc-108">Kullanıcılar ayrıca, ilişkili satır, sütun veya üst bilgi bandı içeriğine göre otomatik olarak yeniden boyutlandırmak için bir bölüye çift tıklabilirler.</span><span class="sxs-lookup"><span data-stu-id="820fc-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="820fc-109">`DataGridView` denetimi, bu kullanıcıya yönelik bu davranışları özelleştirmenize veya devre dışı bırakmanızı sağlayan özellikler, Yöntemler ve olaylar sağlar.</span><span class="sxs-lookup"><span data-stu-id="820fc-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="820fc-110">Ayrıca, satırları, sütunları ve üst bilgileri programlı olarak içeriğe uyacak şekilde yeniden boyutlandırabilir ya da bunların içerikleri değiştiğinde otomatik olarak yeniden boyutlandırılacak şekilde yapılandırma yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="820fc-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="820fc-111">Ayrıca sütunları, denetimin kullanılabilir genişliğini belirttiğiniz oranlara göre otomatik olarak bölmek için de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="820fc-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="820fc-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="820fc-112">In This Section</span></span>  
 [<span data-ttu-id="820fc-113">Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="820fc-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="820fc-114">Satırları, sütunları ve başlıkları boyutlandırma seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="820fc-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="820fc-115">Ayrıca, boyutlandırma ile ilgili özellikler ve yöntemler hakkında ayrıntılar sağlar ve yaygın kullanım senaryolarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="820fc-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="820fc-116">Windows Forms DataGridView Denetiminde Sütun Doldurma Modu</span><span class="sxs-lookup"><span data-stu-id="820fc-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="820fc-117">Sütun dolgusu modunu ayrıntılı olarak açıklar ve sütun dolgusu modunu ve diğer modlarını denemek için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="820fc-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="820fc-118">Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="820fc-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="820fc-119">Genel amaçlar için boyutlandırma modlarının nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="820fc-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="820fc-120">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçeriği Sığdıracak Şekilde Hücreleri Programlı Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="820fc-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="820fc-121">Programlı yeniden boyutlandırmayı denemek için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="820fc-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="820fc-122">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçerik Değiştiğinde Hücreleri Otomatik Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="820fc-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="820fc-123">Otomatik boyutlandırma modlarıyla denemeler yapmak için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="820fc-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="820fc-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="820fc-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="820fc-125"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="820fc-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820fc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="820fc-126">See also</span></span>

- [<span data-ttu-id="820fc-127">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="820fc-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
