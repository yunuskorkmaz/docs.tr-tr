---
title: 'Nasıl yapılır: FontSizeConverter Sınıfını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 7cb76ad4ffe4b4574a48212240b852e1f2253088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741905"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Nasıl yapılır: FontSizeConverter Sınıfını Kullanma
## <a name="example"></a>Örnek  
 Bu örnek, bir örneğini oluşturma işlemi gösterilmektedir <xref:System.Windows.FontSizeConverter> ve yazı tipi boyutunu değiştirmek için kullanabilirsiniz.  
  
 Örnek olarak adlandırılan özel bir yöntem tanımlar `changeSize` içeriğini dönüştüren bir <xref:System.Windows.Controls.ListBoxItem>, ayrı bir tanımlandığı şekilde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasına örneği <xref:System.Double>daha sonrada bir <xref:System.String>. Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.FontSizeConverter> dönüştüren nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Double>. Bu değer daha sonra geri değeri olarak geçirilir <xref:System.Windows.Controls.TextBlock.FontSize%2A> özelliği <xref:System.Windows.Controls.TextBlock> öğesi.  
  
 Bu örnek ayrıca çağrılan özel bir ikinci yöntem tanımlar `changeFamily`. Bu yöntem dönüştürür <xref:System.Windows.Controls.ContentControl.Content%2A> , <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.String>ve ardından bu değeri geçirir <xref:System.Windows.Controls.TextBlock.FontFamily%2A> özelliği <xref:System.Windows.Controls.TextBlock> öğesi.  
  
 Bu örnek çalışmaz.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.FontSizeConverter>
