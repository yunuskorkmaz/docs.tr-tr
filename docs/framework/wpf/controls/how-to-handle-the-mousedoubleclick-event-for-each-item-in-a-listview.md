---
title: "Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962072"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme
İçindeki <xref:System.Windows.Controls.ListView>bir öğeye yönelik bir olayı işlemek için, her birine <xref:System.Windows.Controls.ListViewItem>bir olay işleyicisi eklemeniz gerekir. Bir <xref:System.Windows.Controls.ListView> veri kaynağına bağlandığında, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturmazsınız, ancak bir stil <xref:System.Windows.EventSetter> <xref:System.Windows.Controls.ListViewItem>öğesine ekleyerek her öğe için olayını işleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir veri sınırı <xref:System.Windows.Controls.ListView> oluşturur ve her birine <xref:System.Windows.Controls.ListViewItem>bir <xref:System.Windows.Style> olay işleyicisi eklemek için bir oluşturur.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki örnek <xref:System.Windows.Controls.Control.MouseDoubleClick> olayı işler.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Bir veri <xref:System.Windows.Controls.ListView> kaynağına bağlamak en yaygın olsa da, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturup oluşturmasanız <xref:System.Windows.Controls.ListView> ne olursa olsun, her birine <xref:System.Windows.Controls.ListViewItem> bir olay işleyicisi eklemek için bir stil kullanabilirsiniz.  Açık ve örtük olarak oluşturulan <xref:System.Windows.Controls.ListViewItem> denetimler hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlElement>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView Genel Bakış](listview-overview.md)
