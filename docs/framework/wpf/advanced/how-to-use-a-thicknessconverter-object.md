---
title: "Nasıl yapılır: ThicknessConverter Nesnesi Kullanma"
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
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ce70dcd749f31d77061b4669d83d2e0b83726c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-thicknessconverter-object"></a>Nasıl yapılır: ThicknessConverter Nesnesi Kullanma
## <a name="example"></a>Örnek  
 Bu örnek bir örneğini oluşturmak nasıl gösterir <xref:System.Windows.ThicknessConverter> ve kalınlığını değiştirmek için kullanın.  
  
 Örnek olarak adlandırılan özel bir yöntem tanımlar `changeThickness`; bu yöntem ilk içeriklerini dönüştürür bir <xref:System.Windows.Controls.ListBoxItem>, ayrı bir tanımlanan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasına örneği <xref:System.Windows.Thickness>ve daha sonra içeriği olarak dönüştürür bir <xref:System.String>. Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.ThicknessConverter> dönüştürür Nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Windows.Thickness>. Bu değer daha sonra değeri olarak geri geçirilir <xref:System.Windows.Controls.Border.BorderThickness%2A> özelliği <xref:System.Windows.Controls.Border>.  
  
 Bu örnek çalışmaz.  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [Nasıl yapılır: kenar boşluğu özelliğini değiştirme](http://msdn.microsoft.com/en-us/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [Nasıl yapılır: ListBoxItem yeni bir veri türüne dönüştürün](http://msdn.microsoft.com/en-us/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [Paneller Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
