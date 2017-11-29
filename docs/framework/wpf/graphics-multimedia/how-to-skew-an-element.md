---
title: "Nasıl yapılır: Bir Öğeyi Eğme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5c46b8c64a26d83ba6d8f018b9a1f8ca8250a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-skew-an-element"></a>Nasıl yapılır: Bir Öğeyi Eğme
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.SkewTransform> bir öğeyi eğme için. Olarak da bilinen bükme olduğundan, bir eğme koordinat Tekdüzen olmayan bir biçimde uzatan bir dönüşümü gerçekleşir. Tipik bir kullanımı, bir <xref:System.Windows.Media.SkewTransform> benzetimi yapmasıdır [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] derinlemesine [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] nesneleri.  
  
 Kullanım <xref:System.Windows.Media.SkewTransform.CenterX%2A> ve <xref:System.Windows.Media.SkewTransform.CenterY%2A> center belirtmek için özellikleri noktasını <xref:System.Windows.Media.SkewTransform>.  
  
 Kullanım <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> özellikleri x ve y ekseni eğme açısını belirtmek ve bu eksen boyunca geçerli koordinat sistemi eğme.  
  
 Bir eğme dönüştürmesi etkisini tahmin etmek için göz önünde bulundurun <xref:System.Windows.Media.SkewTransform.AngleX%2A> x ekseni değerleri özgün koordinat sistemi göre Eğer. Bu nedenle, bir <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, y ekseni kaynağı üzerinden 30 derece döner ve değerlerini x-kaynağından 30 derece eğer. Benzer şekilde, bir <xref:System.Windows.Media.SkewTransform.AngleY%2A> şeklin y değerleri 30 kaynaktan 30 derece eğer. Bu (taşıma) çevirme aynı etkiye olmadığını unutmayın 30 derece x ve y koordinat sistemi.  
  
 Aşağıdaki örnekte, 45 derece yatay eğme uygulanır bir <xref:System.Windows.Shapes.Rectangle> merkezi noktasından (0,0).  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Aşağıdaki örnekte, 45 derece yatay eğme uygulanır bir <xref:System.Windows.Shapes.Rectangle> merkezi noktasından (25,25).  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Aşağıdaki örnekte, 45 derece dikey eğme uygulanır bir <xref:System.Windows.Shapes.Rectangle> merkezi noktasından (25,25).  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Aşağıdaki çizimde, bu örnekte kullanılır farklı eğriltir gösterir.  
  
 ![SkewTransform örnekleri](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Gösterilen üç SkewTransform örneği  
  
 Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [Dönüşümler genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
