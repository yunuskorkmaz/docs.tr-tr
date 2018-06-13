---
title: 'Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 689b73eb58cdfceb2ce5d4e76cbbc3d6c5af8967
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551810"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme
Bu konuda nasıl ayarlanacağını açıklar <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar> sabit bir boyuta ve için en az bir boyut belirlemek nasıl <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> sabit bir boyuta sahip. Örnek <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> özelliği <xref:System.Windows.Controls.Primitives.Thumb> için <xref:System.Double.NaN> ve yüksekliğini ayarlar <xref:System.Windows.Controls.Primitives.Thumb>.  Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> sabit genişliği olan, genişliğini ayarla <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> minimum boyutu. Örnek değerini ayarlar <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> en küçük genişliği olan, Ayarla <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ScrollBar Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
