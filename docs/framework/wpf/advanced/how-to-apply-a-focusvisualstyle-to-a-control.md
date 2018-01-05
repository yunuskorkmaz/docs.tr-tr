---
title: "Nasıl yapılır: Denetime FocusVisualStyle Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41895974b7e6c128d979e362f2dcef1c68e0a5c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Nasıl yapılır: Denetime FocusVisualStyle Uygulama
Bu örnek kaynaklarında odak görsel stili oluşturmak ve bir denetim için stil uygulamak gösterilmiştir kullanarak <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bu denetim nde klavye odaklı olduğunda uygulanan ek denetim birleştirmesini oluşturur bir stil tanımlar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Bu bir stille tanımlayarak gerçekleştirilir bir <xref:System.Windows.Controls.ControlTemplate>, bu stili ayarlarken bir kaynak olarak başvuran sonra <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.  
  
 Kenarlık benzeyen bir dış dikdörtgen dikdörtgen dışında yerleştirilir. Aksi değiştirilmediği sürece, stil boyutlandırma kullanır <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> dikdörtgen denetiminin odak görsel stil burada uygulanır. Bu örnek için negatif değerler ayarlar <xref:System.Windows.FrameworkElement.Margin%2A> biraz daha odaklı denetimin dışında görünür kenarlık yapma.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> olan gelen herhangi bir denetim şablonu stil eklenebilir ya da bir açık stili veya bir tema stili; denetimi için birincil stil hala kullanarak oluşturulabilir bir <xref:System.Windows.Controls.ControlTemplate> ve bu stili ayarını <xref:System.Windows.FrameworkElement.Style%2A> özelliği.  
  
 Görsel stiller kullanılmalıdır tutarlı bir tema veya bir kullanıcı Arabirimi odak odaklanabilir her öğe için farklı bir kullanarak yerine. Ayrıntılar için bkz [denetimleri ve FocusVisualStyle odakta için stil oluşturma](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
