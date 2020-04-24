---
title: "Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646105"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme
Bir öğenin olaylarını işlemek <xref:System.Windows.Controls.ListView>için, her <xref:System.Windows.Controls.ListViewItem>birine bir olay işleyicisi eklemeniz gerekir. A <xref:System.Windows.Controls.ListView> bir veri kaynağına bağlandığında, açıkça bir <xref:System.Windows.Controls.ListViewItem>, ancak bir <xref:System.Windows.EventSetter> . <xref:System.Windows.Controls.ListViewItem>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veriye bağlı <xref:System.Windows.Controls.ListView> bir oluşturur <xref:System.Windows.Style> ve her <xref:System.Windows.Controls.ListViewItem>birine bir olay işleyicisi eklemek için bir tane oluşturur.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki örnek <xref:System.Windows.Controls.Control.MouseDoubleClick> olayı işler.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Bir veri <xref:System.Windows.Controls.ListView> kaynağına a bağlamak en yaygın olsa da, açıkça bir tane oluşturup oluşturmadığınıza bakılmaksızın, her <xref:System.Windows.Controls.ListViewItem> birine veri ye bağlı <xref:System.Windows.Controls.ListView> olmayan bir olay işleyicisi eklemek için bir <xref:System.Windows.Controls.ListViewItem>stil kullanabilirsiniz.  Açık ve örtülü olarak oluşturulan <xref:System.Windows.Controls.ListViewItem> denetimler <xref:System.Windows.Controls.ItemsControl>hakkında daha fazla bilgi için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlElement>
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XMLDataProvider ve XPath Sorguları Kullanarak XML Verilerine Bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView Genel Bakış](listview-overview.md)
