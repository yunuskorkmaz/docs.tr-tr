---
title: "Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae76d33a30853107cbecf0749230aefce77a866d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-an-element-spin-in-place"></a>Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama
Bu örnek kullanarak döndürme bir öğe nasıl yapılacağını gösterir bir <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Aşağıdaki örnek uygular <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesi özelliği. Örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon için <xref:System.Windows.Media.RotateTransform.Angle%2A> , <xref:System.Windows.Media.RotateTransform>. Yerinde öğeyi göstermek için örnek ayarlar <xref:System.Windows.UIElement.RenderTransformOrigin%2A> (0,5, 0,5) noktasına öğesi özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Daha fazla dönüşüm örnekleri içeren tam örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
