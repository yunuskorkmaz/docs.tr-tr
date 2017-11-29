---
title: "Nasıl yapılır: FrameworkElement Boyutuna Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17882494e48c5d692c8a774e6d77408557976c71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Nasıl yapılır: FrameworkElement Boyutuna Animasyon Ekleme
Boyutunu animasyon uygulamak için bir <xref:System.Windows.FrameworkElement>, animasyon ya da kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri veya kullanım animasyonlu <xref:System.Windows.Media.ScaleTransform>.  
  
 Aşağıdaki örnekte, bu iki yaklaşım kullanarak iki düğmenin boyutunu canlandırır. Bir düğme yeniden boyutlandırılır animasyon tarafından kendi <xref:System.Windows.FrameworkElement.Width%2A> özelliği ve başka bir yeniden boyutlandırılır animasyon tarafından bir <xref:System.Windows.Media.ScaleTransform> uygulanan kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği. Her düğme bazı metinler içerir. Başlangıçta, metin hem düğmeleri aynı görünür, ancak düğmeler yeniden boyutlandırıldığında gibi ikinci düğme metni bozulur.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Bir öğenin dönüştürme, öğenin tamamını ve içeriği dönüştürülür. İlk düğme durumunda olduğu gibi bir öğenin boyutunu doğrudan değiştirdiğinizde, boyutunu ve konumunu kendi üst öğesi boyutuna göre değişir sürece öğenin içeriği yeniden boyutlandırılıyor değil.  
  
 Animasyonlu dönüşüm uygulayarak bir öğenin boyutunu animasyon kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği animasyonlu daha iyi performans sağlar, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> doğrudan, çünkü <xref:System.Windows.UIElement.RenderTransform%2A> özelliği düzen geçişini tetiklemez.  
  
 Özellikleri hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Dönüşümler hakkında daha fazla bilgi için bkz: [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).
