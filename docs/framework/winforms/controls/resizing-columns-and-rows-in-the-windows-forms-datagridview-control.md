---
title: Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: e1fa2d57cfb2cd374d691fe03a0e0bdbd3ad7141
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138118"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="afc69-102">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="afc69-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="afc69-103">`DataGridView` Denetim satırları ve sütunları boyutlandırma davranışını özelleştirmek için çeşitli seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc69-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="afc69-104">Genellikle, `DataGridView` hücreleri değil yeniden boyutlandırma, içeriğine göre.</span><span class="sxs-lookup"><span data-stu-id="afc69-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="afc69-105">Bunun yerine, hücreden daha büyük herhangi bir görüntü değeriyle küçük.</span><span class="sxs-lookup"><span data-stu-id="afc69-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="afc69-106">İçerik bir dize olarak görüntülenebilir, hücre bir araç ipucu olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="afc69-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="afc69-107">Varsayılan olarak, kullanıcılar, satır ve sütun üst bilgisi Bölücü daha fazla bilgi görüntülemek için fareyle sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afc69-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="afc69-108">Kullanıcılar ayrıca kendi içeriklerini temel alarak ilişkili satır, sütun veya üstbilgi bant otomatik olarak yeniden boyutlandırmak için bir ayırıcı çift tıklatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afc69-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="afc69-109">`DataGridView` Denetimi özellikleri, yöntemleri ve özelleştirme ya da tüm bu kullanıcıyı yönlendiren davranışların devre dışı etkinleştiren olayları sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc69-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="afc69-110">Ayrıca, satırlar, sütunlar ve bunların içeriğini sığdırmak için üst bilgileri programlı bir şekilde boyutlandırabilirsiniz veya içerikleri değiştiğinde kendilerini otomatik olarak yeniden yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afc69-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="afc69-111">Sütunları otomatik olarak belirttiğiniz oranlarını denetimi kullanılabilir genişliğini bölmek için de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afc69-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afc69-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="afc69-112">In This Section</span></span>  
 [<span data-ttu-id="afc69-113">Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="afc69-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="afc69-114">Boyutlandırma satırlar, sütunlar ve üst bilgileri için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="afc69-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="afc69-115">Ayrıca boyutlandırma ile ilgili özellikleri ve yöntemleri hakkında ayrıntılar sağlar ve genel kullanım senaryoları açıklar.</span><span class="sxs-lookup"><span data-stu-id="afc69-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="afc69-116">Windows Forms DataGridView Denetiminde Sütun Doldurma Modu</span><span class="sxs-lookup"><span data-stu-id="afc69-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="afc69-117">Sütun doldurma modu ayrıntılı açıklar ve sütun doldurma modu ve Diğer modları ile denemek için kullanabileceğiniz bir tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc69-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="afc69-118">Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="afc69-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="afc69-119">Genel amaçlar için boyutlandırma modlarını yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="afc69-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="afc69-120">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçeriği Sığdıracak Şekilde Hücreleri Programlı Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="afc69-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="afc69-121">Programlı olarak yeniden boyutlandırma ile denemek için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc69-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="afc69-122">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçerik Değiştiğinde Hücreleri Otomatik Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="afc69-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="afc69-123">Otomatik boyutlandırma modları ile denemek için kullanabileceğiniz tanıtım kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc69-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="afc69-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="afc69-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="afc69-125">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="afc69-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc69-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afc69-126">See also</span></span>

- [<span data-ttu-id="afc69-127">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="afc69-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
