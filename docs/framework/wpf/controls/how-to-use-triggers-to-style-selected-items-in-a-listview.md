---
title: 'Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: ad64382b871bae9114a1e63257de3f8595376923
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696205"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="8c8f1-102">Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="8c8f1-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="8c8f1-103">Bu örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Style.Triggers%2A> için bir <xref:System.Windows.Controls.ListViewItem> denetim böylece bir özellik değeri, bir <xref:System.Windows.Controls.ListViewItem> değişiklikleri <xref:System.Windows.Style> , <xref:System.Windows.Controls.ListViewItem> değişiklikleri yanıt.</span><span class="sxs-lookup"><span data-stu-id="8c8f1-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c8f1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c8f1-104">Example</span></span>  
 <span data-ttu-id="8c8f1-105">İsterseniz <xref:System.Windows.Style> , bir <xref:System.Windows.Controls.ListViewItem> özelliği değişikliklere yanıt olarak değiştirmek için tanımladığınız <xref:System.Windows.Style.Triggers%2A> için <xref:System.Windows.Style> değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8c8f1-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="8c8f1-106">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Trigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliğini <xref:System.Windows.Media.Brushes.Blue%2A> ve değişiklikleri <xref:System.Windows.FrameworkElement.Cursor%2A> görüntülemek için bir <xref:System.Windows.Input.CursorType.Hand> olduğunda <xref:System.Windows.UIElement.IsMouseOver%2A> özellik değişiklikleri `true`.</span><span class="sxs-lookup"><span data-stu-id="8c8f1-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="8c8f1-107">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.MultiTrigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.ListViewItem> için <xref:System.Windows.Media.Brushes.Yellow%2A> olduğunda <xref:System.Windows.Controls.ListViewItem> seçili öğe ve klavye girintisine sahip.</span><span class="sxs-lookup"><span data-stu-id="8c8f1-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="8c8f1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c8f1-108">See also</span></span>

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="8c8f1-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="8c8f1-109">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="8c8f1-110">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8c8f1-110">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="8c8f1-111">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8c8f1-111">GridView Overview</span></span>](gridview-overview.md)
