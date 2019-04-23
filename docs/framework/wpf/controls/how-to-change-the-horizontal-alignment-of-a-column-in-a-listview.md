---
title: 'Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 528a711c1cf7992bb32c0aa4d6e81d71744c9f80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102667"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme
Varsayılan olarak, her bir sütunun içeriğine bir <xref:System.Windows.Controls.ListViewItem> sola hizalanır. Her sütunun hizalamasını sağlayarak değiştirebileceğiniz bir <xref:System.Windows.DataTemplate> ve ayarı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> içindeki öğe üzerinde özellik <xref:System.Windows.DataTemplate>. Bu konu başlığı altında gösterilir nasıl bir <xref:System.Windows.Controls.ListView> içeriğini varsayılan ve içerisindeki bir sütunun hizalamasını değiştirme göre hizalar bir <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, verileri `Title` ve `ISBN` sütunları sola hizalıdır.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Hizalamasını değiştirmek için `ISBN` sütun ihtiyacınız olduğunu belirtmek <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> her özellik <xref:System.Windows.Controls.ListViewItem> olan <xref:System.Windows.HorizontalAlignment.Stretch>, böylece her öğe <xref:System.Windows.Controls.ListViewItem> yayılabilir veya tüm her sütunun genişliği boyunca konumlandırılabilir. Çünkü <xref:System.Windows.Controls.ListView> bağlı ayarlayan bir stil oluşturmak gereken bir veri kaynağına <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Ardından, kullanmak gereken bir <xref:System.Windows.DataTemplate> kullanmak yerine içeriği görüntülemek için <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> özelliği. Görüntülenecek `ISBN` her şablonunun <xref:System.Windows.DataTemplate> yalnızca içerebilir bir <xref:System.Windows.Controls.TextBlock> olan kendi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini <xref:System.Windows.HorizontalAlignment.Right>.  
  
 Aşağıdaki örnek, stil tanımlar ve <xref:System.Windows.DataTemplate> yapmak gerekli `ISBN` sağa hizalanmış sütun ve değişiklikleri <xref:System.Windows.Controls.GridViewColumn> başvurusuna <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView Genel Bakış](listview-overview.md)
