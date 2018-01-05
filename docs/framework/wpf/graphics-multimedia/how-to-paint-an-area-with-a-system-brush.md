---
title: "Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87979c16d52262c665e2fb37fdf6d7550c5930c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama
<xref:System.Windows.SystemColors> Sınıfı sistem fırçaları ve renkler, erişim gibi sağlar <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, ve <xref:System.Windows.SystemColors.DesktopBrush%2A>. Sistem Fırçası olan bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renk ile alanı boyar nesnesi. Sistem Fırçası her zaman bir düz dolgu üretir; gradyan oluşturmak için kullanılamaz.  
  
 Sistem fırçaları statik veya dinamik bir kaynak kullanabilirsiniz. Uygulama çalışırken kullanıcı sistem fırçası değiştirirse otomatik olarak güncelleştirmek için fırça istiyorsanız, dinamik kaynak kullanın; Aksi halde, bir statik kaynak kullanın. SystemColors sınıfı çeşitli sıkı bir adlandırma kuralı izleyin statik özellikler içerir:  
  
-   *\<SystemColor >*fırça  
  
     Statik başvuru alır bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renginin.  
  
-   *\<SystemColor >*BrushKey  
  
     Dinamik bir başvuru edinir bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renginin.  
  
-   *\<SystemColor >*rengi  
  
     Statik başvuru alır bir <xref:System.Windows.Media.Color> belirtilen sistem renginin yapısını.  
  
-   *\<SystemColor >*ColorKey  
  
     Dinamik bir başvuru edinir <xref:System.Windows.Media.Color> belirtilen sistem renginin yapısını.  
  
 Sistem rengi bir <xref:System.Windows.Media.Color> fırça yapılandırmak için kullanılan yapısı. Örneğin, sistem renkleri ayarlayarak kullanan bir gradyan oluşturabilirsiniz <xref:System.Windows.Media.GradientStop.Color%2A> özelliklerini bir <xref:System.Windows.Media.LinearGradientBrush> nesnesi gradyan duraklarının sistem renklerle. Bir örnek için bkz: [gradyan Sistem renklerini kullan](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir düğmenin arka planını ayarlamak için dinamik sistem fırçası başvurusunu kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 Sonraki örnek bir düğmenin arka planını ayarlamak için bir statik sistem fırçası başvurusunu kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Bir sistem renginin bir gradyan içerisinde nasıl kullanılacağını gösteren bir örnek için bkz: [Sistem renklerini kullan gradyan](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sistem Renklerinin Gradyan İçinde Kullanımı](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
