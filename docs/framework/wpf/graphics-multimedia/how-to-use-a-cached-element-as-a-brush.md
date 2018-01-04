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
ms.workload: dotnet
ms.openlocfilehash: f463c15855e267a4c246625a8d06e627852f48a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [Nasıl yapılır: Öğeyi Önbelleğe Alarak İşleme Performansını Artırma](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
