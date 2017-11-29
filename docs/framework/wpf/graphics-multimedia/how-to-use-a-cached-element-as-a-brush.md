---
title: "Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d0f0c60e9df6a1ec816b1f9cf5769c93b382ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma
Kullanım <xref:System.Windows.Media.BitmapCacheBrush> önbelleğe alınan öğeyi verimli bir şekilde yeniden sınıfı. Bir öğenin önbelleğe almak için yeni bir örneğini oluşturmak <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, önbelleğe alınan öğe yeniden gösterilmektedir. Önbelleğe alınan öğe bir <xref:System.Windows.Controls.Image> büyük bir görüntü görüntüleyen denetim. <xref:System.Windows.Controls.Image> Denetim önbelleğe alınma bir bit eşlem olarak kullanarak <xref:System.Windows.Media.BitmapCache> sınıfı ve önbellek yeniden atayarak bunu bir <xref:System.Windows.Media.BitmapCacheBrush>. Fırça etkili bir biçimde yeniden göstermek için yirmi beş düğmelerinin arka plan atanır.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Nasıl yapılır: performans öğenin önbelleğe alarak işleme geliştirmek](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
