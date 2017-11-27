---
title: "Nasıl yapılır: Öğeler ve Denetimlerin Kenar Boşluklarını Ayarlama"
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
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 965e2061d6457084e4f316d27e29865109f62e34
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>Nasıl yapılır: Öğeler ve Denetimlerin Kenar Boşluklarını Ayarlama
Bu örnek nasıl ayarlanacağını açıklar <xref:System.Windows.FrameworkElement.Margin%2A> arka plan kodu boşlukta için herhangi bir varolan özellik değerini değiştirerek özelliği. <xref:System.Windows.FrameworkElement.Margin%2A> Özelliği bir özelliğidir <xref:System.Windows.FrameworkElement> temel öğesi ve bu nedenle çeşitli denetimler ve diğer öğeler tarafından devralınır.  
  
 Bu örnekte yazılan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir arka plan kodu ile dosya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvuruyor. Arka plan kodu hem de gösterilen bir [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] ve [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] sürümü.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
