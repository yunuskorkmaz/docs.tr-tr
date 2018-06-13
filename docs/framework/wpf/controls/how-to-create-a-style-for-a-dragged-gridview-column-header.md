---
title: 'Nasıl yapılır: Sürüklenen GridView Sütun Başlığı için Stil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 2e57b4cb1b8ddb90e8e6e0abc6db3e7f0b864cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554579"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="6e337-102">Nasıl yapılır: Sürüklenen GridView Sütun Başlığı için Stil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e337-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="6e337-103">Bu örnek sürüklenen görünüşünü değiştirme gösterilmektedir <xref:System.Windows.Controls.GridViewColumnHeader> kullanıcı bir sütunun konumunu değiştiğinde.</span><span class="sxs-lookup"><span data-stu-id="6e337-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e337-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e337-104">Example</span></span>  
 <span data-ttu-id="6e337-105">Başka bir konumda bir sütun başlığını sürüklediğinizde bir <xref:System.Windows.Controls.ListView> kullanan <xref:System.Windows.Controls.GridView> görünüm modu için sütun yeni bir konuma taşır.</span><span class="sxs-lookup"><span data-stu-id="6e337-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="6e337-106">Sütun başlığını sürükleme sırasında üstbilgi kayan bir kopyasını özgün üstbilgisi yanı sıra görünür.</span><span class="sxs-lookup"><span data-stu-id="6e337-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="6e337-107">Bir sütun başlığına bir <xref:System.Windows.Controls.GridView> tarafından temsil edilen bir <xref:System.Windows.Controls.GridViewColumnHeader> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6e337-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="6e337-108">Kayan ve özgün başlıkların görünümünü özelleştirmek için ayarlayabileceğiniz <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> değiştirmek için <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="6e337-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="6e337-109">Bunlar <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> ne zaman uygulanacağını <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> özellik değeri `true` ve <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özellik değeri <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="6e337-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="6e337-110">Ne zaman kullanıcının fare düğmesini tıklatıp üzerinde fare duraklatır sırada tuttuğu <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> özellik değeri değişiklikleri `true`.</span><span class="sxs-lookup"><span data-stu-id="6e337-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="6e337-111">Benzer şekilde, kullanıcı başladığı sürükleme işlemi <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özelliği değişiklikler <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="6e337-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="6e337-112">Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> değiştirmek için <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.Background%2A> kullanıcı yeni bir konuma bir sütun sürüklendiğinde özgün ve kayan başlıkların renklerini.</span><span class="sxs-lookup"><span data-stu-id="6e337-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="6e337-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e337-113">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="6e337-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="6e337-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="6e337-115">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6e337-115">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="6e337-116">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6e337-116">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
