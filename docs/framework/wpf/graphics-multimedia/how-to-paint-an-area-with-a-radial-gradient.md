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
ms.openlocfilehash: c3bcc11dea4b1f223f629415591ab03588881dde
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379789"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.RadialGradientBrush> Radyal gradyan ile bir alanı boyama için sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.RadialGradientBrush> sarı kırmızı, mavi yeşile geçiş Radyal gradyan ile bir dikdörtgen boyamak için.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Önceki örnekte gradyan aşağıda gösterilmiştir. Gradyan duraklarını vurgulanır.  
  
 ![Radyal gradyan gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  Bu konudaki örnekler varsayılan koordinat sistemi denetim noktalarını ayarlamak için kullanın. Varsayılan koordinat sistemi göreli bir sınırlayıcı kutu şöyledir: 0 gösterir sınırlayıcı kutusunun yüzde 0 ve 1, sınırlayıcı kutunun yüzde 100 gösterir. Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özellik değerine <xref:System.Windows.Media.BrushMappingMode.Absolute>. Mutlak koordinat sistemi bir sınırlayıcı kutu göreli değil. Değerleri, doğrudan yerel alan yorumlanır.  
  
 İçin ek <xref:System.Windows.Media.RadialGradientBrush> örnekler [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973). Gradyanlar ve diğer türleri Fırçalar hakkında daha fazla bilgi için bkz: [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md).
