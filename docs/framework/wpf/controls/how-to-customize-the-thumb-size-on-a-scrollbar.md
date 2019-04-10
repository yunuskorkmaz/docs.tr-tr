---
title: 'Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 60ae7c4e95801036c5deb0c485645297509b830c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207285"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme
Bu konu nasıl ayarlanacağını açıklar <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar> sabit bir boyuta ve için en az bir boyut belirlemek nasıl <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> sabit bir boyuta sahip. Örnek <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> özelliği <xref:System.Windows.Controls.Primitives.Thumb> için <xref:System.Double.NaN> ve yüksekliğini ayarlar <xref:System.Windows.Controls.Primitives.Thumb>.  Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> genişliğini ayarlamak, sabit genişlik olan <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> en küçük boyutu. Örnek ayarlar <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> ayarlayın, en küçük genişliği olan <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ScrollBar Stilleri ve Şablonları](scrollbar-styles-and-templates.md)
