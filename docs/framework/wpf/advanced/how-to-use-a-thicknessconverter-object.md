---
title: 'Nasıl yapılır: ThicknessConverter Nesnesi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: ebfb8642a01f6d602f4e5ffa58fde6a8ee0b4e1f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075957"
---
# <a name="how-to-use-a-thicknessconverter-object"></a>Nasıl yapılır: ThicknessConverter Nesnesi Kullanma
## <a name="example"></a>Örnek  
 Bu örnek, bir örneğini oluşturma işlemi gösterilmektedir <xref:System.Windows.ThicknessConverter> ve kenarlık kalınlığına değiştirmek için kullanabilirsiniz.  
  
 Örnek olarak adlandırılan özel bir yöntem tanımlar `changeThickness`; bu yöntem ilk içeriğini dönüştürür bir <xref:System.Windows.Controls.ListBoxItem>, ayrı bir tanımlandığı şekilde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasına bir örneğini <xref:System.Windows.Thickness>ve daha sonra da içerik bilgisini dönüştüren bir <xref:System.String>. Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.ThicknessConverter> dönüştüren nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Windows.Thickness>. Bu değer daha sonra geri değeri olarak geçirilir <xref:System.Windows.Controls.Border.BorderThickness%2A> özelliği <xref:System.Windows.Controls.Border>.  
  
 Bu örnek çalışmaz.  
  
 [!code-csharp[ThicknessConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- [Nasıl yapılır: Margin özelliği değiştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))
- [Nasıl yapılır: Bir ListBoxItem yeni bir veri türüne dönüştürün](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))
- [Panellere Genel Bakış](../controls/panels-overview.md)
