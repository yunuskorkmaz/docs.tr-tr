---
title: "Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 775d51a35f64f8736931dec32fb439bb9925be53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturma ve kullanma örneği gösterilmiştir <xref:System.Windows.GridLengthConverter>. Örnek olarak adlandırılan özel bir yöntem tanımlar `changeCol`, hangi geçişleri <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.GridLengthConverter> dönüştüren <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Windows.GridLength>. Dönüştürülen değer daha sonra değeri olarak geri geçirilir <xref:System.Windows.Controls.ColumnDefinition.Width%2A> özelliği <xref:System.Windows.Controls.ColumnDefinition> öğesi.  
  
 Örnek ayrıca adlı ikinci bir özel yöntem tanımlar `changeColVal`. Bu özel yöntem dönüştürür <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> , bir <xref:System.Windows.Controls.Slider> için bir <xref:System.String> ve değer başa sonra geçişleri <xref:System.Windows.Controls.ColumnDefinition> olarak <xref:System.Windows.Controls.ColumnDefinition.Width%2A> öğesi.  
  
 Unutmayın ayrı bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya içeriğini tanımlayan bir <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
