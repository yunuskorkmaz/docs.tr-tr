---
title: 'Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 5447f1a73b008b2ed4f345eba00f4d631e11e257
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458597"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme
Varsayılan olarak, bir <xref:System.Windows.Controls.ListViewItem> her sütunun içeriği sola hizalanır. Her sütunun hizalamasını, bir <xref:System.Windows.DataTemplate> sağlayarak ve <xref:System.Windows.DataTemplate>içindeki öğe üzerinde <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini ayarlayarak değiştirebilirsiniz. Bu konu, bir <xref:System.Windows.Controls.ListView> içeriğini varsayılan olarak nasıl hizaladığını ve bir sütunun bir <xref:System.Windows.Controls.ListView>hizalamasını nasıl değiştirileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Title` ve `ISBN` sütunlarındaki veriler sola hizalanır.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 `ISBN` sütununun hizalamasını değiştirmek için, her bir <xref:System.Windows.Controls.ListViewItem> <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> özelliğinin <xref:System.Windows.HorizontalAlignment.Stretch>olduğunu belirtmeniz gerekir, böylece her bir <xref:System.Windows.Controls.ListViewItem> içindeki öğelerin her bir sütunun genişliğinin tamamına yayılabilmesini veya konumlandırılabilmesini sağlayabilirsiniz. <xref:System.Windows.Controls.ListView> bir veri kaynağına bağlandığı için, <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>ayarlayan bir stil oluşturmanız gerekir. Sonra, <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> özelliğini kullanmak yerine içeriği göstermek için bir <xref:System.Windows.DataTemplate> kullanmanız gerekir. Her şablonun `ISBN` göstermek için <xref:System.Windows.DataTemplate>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliği <xref:System.Windows.HorizontalAlignment.Right>olarak ayarlanmış bir <xref:System.Windows.Controls.TextBlock> içerebilir.  
  
 Aşağıdaki örnek, `ISBN` sütununu sağa hizalı hale getirmek için gereken stili ve <xref:System.Windows.DataTemplate> tanımlar ve <xref:System.Windows.Controls.GridViewColumn> <xref:System.Windows.DataTemplate>başvuracak şekilde değiştirir.  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView Genel Bakış](listview-overview.md)
