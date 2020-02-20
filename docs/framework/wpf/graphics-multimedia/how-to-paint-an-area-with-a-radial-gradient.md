---
title: 'Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452759"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama
Bu örnek, radyal gradyan ile bir alanı boyamak için <xref:System.Windows.Media.RadialGradientBrush> sınıfını nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sarıdan kırmızıya ve sıfırdan yeşil 'e geçiş yapan bir radyal degradeyle bir dikdörtgeni boyamak için bir <xref:System.Windows.Media.RadialGradientBrush> kullanır.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Aşağıdaki çizimde, önceki örnekteki gradyan gösterilmektedir. Degradenin duraklar vurgulandı.  
  
 ![Radyal degradede gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> Bu konudaki örneklerde, denetim noktalarını ayarlamak için varsayılan koordinat sistemi kullanılır. Varsayılan koordinat sistemi bir sınırlayıcı kutuya göredir: 0 sınırlayıcı kutunun yüzde 0 ' ı gösterir ve 1 sınırlayıcı kutunun yüzde 100 ' unu gösterir. <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğini <xref:System.Windows.Media.BrushMappingMode.Absolute>değerine ayarlayarak bu koordinat sistemini değiştirebilirsiniz. Mutlak koordinat sistemi bir sınırlayıcı kutuya göreli değildir. Değerler doğrudan yerel alanda yorumlanır.  
  
 Ek <xref:System.Windows.Media.RadialGradientBrush> örnekler için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Degradeler ve diğer fırça türleri hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).
