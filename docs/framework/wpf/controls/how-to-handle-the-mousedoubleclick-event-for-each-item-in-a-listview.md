---
title: "Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 443e5c620ef5bf240d3e317f0234aac0b29b456f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145086"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme
Bir öğe için bir olayı işlemek için bir <xref:System.Windows.Controls.ListView>, her bir olay işleyicisi eklemek gereken <xref:System.Windows.Controls.ListViewItem>. Olduğunda bir <xref:System.Windows.Controls.ListView> bağlı açıkça oluşturmayın bir veri kaynağına bir <xref:System.Windows.Controls.ListViewItem>, ancak ekleyerek her öğe için olayını işleyebilirsiniz bir <xref:System.Windows.EventSetter> stili için bir <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir veri bağlama oluşturur <xref:System.Windows.Controls.ListView> ve oluşturan bir <xref:System.Windows.Style> her bir olay işleyicisi eklemek için <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki örnek tutamaçları <xref:System.Windows.Controls.Control.MouseDoubleClick> olay.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  Bağlamak için en yaygın olmasına rağmen bir <xref:System.Windows.Controls.ListView> bir veri kaynağı için her bir olay işleyicisi eklemek için bir stil kullanabilirsiniz <xref:System.Windows.Controls.ListViewItem> bir olmayan-verilere bağlı olarak <xref:System.Windows.Controls.ListView> olup olmadığını açıkça oluşturma bağımsız olarak bir <xref:System.Windows.Controls.ListViewItem>.  Hakkında daha fazla bilgi için açık ve örtük olarak oluşturulan <xref:System.Windows.Controls.ListViewItem> denetimlerini, <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlElement>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView Genel Bakışı](listview-overview.md)
