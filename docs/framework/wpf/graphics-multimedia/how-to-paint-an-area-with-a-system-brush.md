---
title: 'Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: 7beaf4370f115a3995c9ca23bb0022bd5b269193
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364118"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama
<xref:System.Windows.SystemColors> Sınıfı sağlar sistem fırçaları ve renkler, erişim gibi <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, ve <xref:System.Windows.SystemColors.DesktopBrush%2A>. Sistem Fırçası olduğu bir <xref:System.Windows.Media.SolidColorBrush> nesnesini belirtilen sistem renk ile bir alanı boyar. Sistem Fırçası her zaman bir tek renk dolgu üretir; gradyan oluşturmak için kullanılamaz.  
  
 Sistem fırçaları statik veya dinamik bir kaynak kullanabilirsiniz. Kullanıcı sistem fırçası değiştirirse uygulama çalışırken otomatik olarak güncelleştirilecek fırça istiyorsanız bir dinamik kaynak kullanın. Aksi takdirde, bir statik kaynak kullanın. SystemColors sınıfı çeşitli katı bir adlandırma kuralını uyguladığınızdan statik özellikler içerir:  
  
-   *\<SystemColor>* Brush  
  
     Statik başvuru alır bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renk.  
  
-   *\<SystemColor >* BrushKey  
  
     Dinamik başvuru alır bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renk.  
  
-   *\<SystemColor >* rengi  
  
     Statik başvuru alır bir <xref:System.Windows.Media.Color> belirtilen sistem renk yapısı.  
  
-   *\<SystemColor >* ColorKey  
  
     Dinamik bir başvuru edinir <xref:System.Windows.Media.Color> belirtilen sistem renk yapısı.  
  
 Sistem rengi bir <xref:System.Windows.Media.Color> fırça yapılandırmak için kullanılan yapısı. Örneğin, bir gradyan ayarlayarak Sistem renkleri kullanarak oluşturabilirsiniz <xref:System.Windows.Media.GradientStop.Color%2A> özelliklerini bir <xref:System.Windows.Media.LinearGradientBrush> nesnesi gradyan duraklarının sistem renkleri. Bir örnek için bkz. [gradyan içinde kullanımı sistem renkleri](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir düğme arka planını ayarlama için dinamik sistem fırçası başvurusu kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 Sonraki örnek, bir düğme arka planını ayarlama için statik sistem fırçası başvurusu kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Bir sistem renginin gradyan içinde nasıl kullanılacağını gösteren bir örnek için bkz: [Sistem renklerini kullan gradyan](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sistem Renklerinin Gradyan İçinde Kullanımı](how-to-use-system-colors-in-a-gradient.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
