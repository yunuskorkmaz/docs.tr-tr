---
title: 'Nasıl yapılır: Öğeler ve Denetimlerin Kenar Boşluklarını Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
ms.openlocfilehash: 41a0f1d025061cc7c1472a831fbbd5ed2f01b043
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>Nasıl yapılır: Öğeler ve Denetimlerin Kenar Boşluklarını Ayarlama
Bu örnek nasıl ayarlanacağını açıklar <xref:System.Windows.FrameworkElement.Margin%2A> arka plan kodu boşlukta için herhangi bir varolan özellik değerini değiştirerek özelliği. <xref:System.Windows.FrameworkElement.Margin%2A> Özelliği bir özelliğidir <xref:System.Windows.FrameworkElement> temel öğesi ve bu nedenle çeşitli denetimler ve diğer öğeler tarafından devralınır.  
  
 Bu örnekte yazılan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir arka plan kodu ile dosya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvuruyor. Arka plan kodu hem C# ve Microsoft Visual Basic sürüm gösterilir.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
