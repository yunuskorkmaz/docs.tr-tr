---
title: 'Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 31ee131e1cbd6e56ce5b0c29085c2d29e65dc40b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553903"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Nasıl yapılır: ListView İçerisindeki Bir Sütunun Yatay Hizalamasını Değiştirme
Varsayılan olarak, her bir sütunun içeriğini bir <xref:System.Windows.Controls.ListViewItem> sola hizalı değil. Her sütunun hizalamasını sağlayarak değiştirebileceğiniz bir <xref:System.Windows.DataTemplate> ve ayarı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> öğe içinde özellikte <xref:System.Windows.DataTemplate>. Bu konuda gösterilmektedir nasıl bir <xref:System.Windows.Controls.ListView> içeriğini varsayılan ve bir sütunda hizalamasını değiştirme hizalar bir <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, verileri `Title` ve `ISBN` sütunları sola hizalı.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Hizalamasını değiştirmek için `ISBN` sütun, belirtmeniz gerekir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> her özellik <xref:System.Windows.Controls.ListViewItem> olan <xref:System.Windows.HorizontalAlignment.Stretch>, böylece her öğeleri <xref:System.Windows.Controls.ListViewItem> kapsayabilir veya her bir sütunun tüm genişliği boyunca konumlandırılabilir. Çünkü <xref:System.Windows.Controls.ListView> bağlı bir veri kaynağına ayarlayan bir stil oluşturmanız gerekir. <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Ardından, kullanılacak ihtiyacınız bir <xref:System.Windows.DataTemplate> kullanmak yerine içeriği görüntülemek için <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> özelliği. Görüntülenecek `ISBN` her şablonunun <xref:System.Windows.DataTemplate> yalnızca içerebilir bir <xref:System.Windows.Controls.TextBlock> olan kendi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini <xref:System.Windows.HorizontalAlignment.Right>.  
  
 Aşağıdaki örnek, stilini tanımlar ve <xref:System.Windows.DataTemplate> yapmak gerekli `ISBN` sütunu sağa hizalı ve değişiklikleri <xref:System.Windows.Controls.GridViewColumn> başvuru <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)
