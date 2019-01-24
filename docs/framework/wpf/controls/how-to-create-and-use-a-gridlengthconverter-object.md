---
title: 'Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: b5ab15df4aaf5f6c4ba7bc7a4b36cc5e122b1320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562068"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir örneğini oluşturup kullanacağınızı gösterilmektedir <xref:System.Windows.GridLengthConverter>. Örnek olarak adlandırılan özel bir yöntem tanımlar `changeCol`, hangi geçişleri <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.GridLengthConverter> dönüştüren <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Windows.GridLength>. Dönüştürülen değer daha sonra geri değeri olarak geçirilir <xref:System.Windows.Controls.ColumnDefinition.Width%2A> özelliği <xref:System.Windows.Controls.ColumnDefinition> öğesi.  
  
 Örnek olarak adlandırılan ikinci özel bir yöntem de tanımlar `changeColVal`. Bu özel yöntem dönüştürür <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> , bir <xref:System.Windows.Controls.Slider> için bir <xref:System.String> ve değeri tekrar sonra geçişleri <xref:System.Windows.Controls.ColumnDefinition> olarak <xref:System.Windows.Controls.ColumnDefinition.Width%2A> öğe.  
  
 Unutmayın ayrı bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya içeriğini tanımlayan bir <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
