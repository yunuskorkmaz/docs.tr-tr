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
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916093"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama
Bu örnek, <xref:System.Windows.Media.RadialGradientBrush> bir radyal gradyan ile bir alanı boyamak için sınıfının nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sarıdan <xref:System.Windows.Media.RadialGradientBrush> kırmızıya ve sıfırdan yeşil 'e geçiş yapan bir radyal degradeyle bir dikdörtgeni boyamak için bir kullanır.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Aşağıdaki çizimde, önceki örnekteki gradyan gösterilmektedir. Degradenin duraklar vurgulandı.  
  
 ![Radyal degradede gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> Bu konudaki örneklerde, denetim noktalarını ayarlamak için varsayılan koordinat sistemi kullanılır. Varsayılan koordinat sistemi bir sınırlayıcı kutuya göredir: 0 sınırlayıcı kutunun yüzde 0 ' ı gösterir ve 1 sınırlayıcı kutunun yüzde 100 ' unu gösterir. <xref:System.Windows.Media.GradientBrush.MappingMode%2A> Özelliği değerine<xref:System.Windows.Media.BrushMappingMode.Absolute>ayarlayarak bu koordinat sistemini değiştirebilirsiniz. Mutlak koordinat sistemi bir sınırlayıcı kutuya göreli değildir. Değerler doğrudan yerel alanda yorumlanır.  
  
 Daha fazla <xref:System.Windows.Media.RadialGradientBrush> örnek için bkz. [fırçalar örneği](https://go.microsoft.com/fwlink/?LinkID=159973). Degradeler ve diğer fırça türleri hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).
