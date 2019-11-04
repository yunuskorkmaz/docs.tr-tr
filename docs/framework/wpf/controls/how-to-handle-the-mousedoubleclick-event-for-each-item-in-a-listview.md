---
title: "Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460221"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme
<xref:System.Windows.Controls.ListView>bir öğeye yönelik bir olayı işlemek için, her bir <xref:System.Windows.Controls.ListViewItem>bir olay işleyicisi eklemeniz gerekir. Bir <xref:System.Windows.Controls.ListView> bir veri kaynağına bağlandığında, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturmazsınız, ancak <xref:System.Windows.Controls.ListViewItem>stiline <xref:System.Windows.EventSetter> ekleyerek her öğe için olayı işleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir veri-bağlantılı <xref:System.Windows.Controls.ListView> oluşturur ve her <xref:System.Windows.Controls.ListViewItem>bir olay işleyicisi eklemek için bir <xref:System.Windows.Style> oluşturur.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki örnek <xref:System.Windows.Controls.Control.MouseDoubleClick> olayını işler.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Bir <xref:System.Windows.Controls.ListView> veri kaynağına bağlamak yaygın olsa da, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturup oluşturmasanız bile, veri bağlama olmayan bir <xref:System.Windows.Controls.ListView> her bir <xref:System.Windows.Controls.ListViewItem> bir olay işleyicisi eklemek için bir stil kullanabilirsiniz.  Açık ve örtük olarak oluşturulmuş <xref:System.Windows.Controls.ListViewItem> denetimleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlElement>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView Genel Bakış](listview-overview.md)
