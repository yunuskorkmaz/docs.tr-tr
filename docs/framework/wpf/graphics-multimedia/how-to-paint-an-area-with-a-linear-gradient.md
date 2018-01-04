---
title: "Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eec4ec2fc7ba99081eaafa6803d20c99bebc6c2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.LinearGradientBrush> doğrusal gradyan ile bir alanı boyamak için sınıf. Aşağıdaki örnekte, <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle> yeşile mavi ve kırmızı sarı geçiş çapraz bir doğrusal gradyan ile boyanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Aşağıdaki çizimde önceki örnek tarafından oluşturulan gradyanı gösterir.  
  
 ![Çapraz doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Değişiklik Yatay doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , <xref:System.Windows.Media.LinearGradientBrush> ' ini (0,0.5) ve (1,0.5)'e. Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> Yatay doğrusal gradyan ile boyanır.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Aşağıdaki çizimde önceki örnek tarafından oluşturulan gradyanı gösterir.  
  
 ![Yatay doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Değişiklik dikey doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , <xref:System.Windows.Media.LinearGradientBrush> ' ini (0.5,0) ve (0.5,1)'e. Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> dikey doğrusal gradyan ile boyanır.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Aşağıdaki çizimde önceki örnek tarafından oluşturulan gradyanı gösterir.  
  
 ![Dikey doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  Bu konudaki örnekler, başlangıç ve bitiş noktalarını ayarlamak için varsayılan koordinat sistemi kullanır. Varsayılan koordinat sistemi göreli bir sınırlama kutusudur: 0 gösterir sınırlayıcı kutusunun yüzde 0 ve 1 sınırlayıcı kutusunun yüzde 100 gösterir. Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğinin değeri <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>. Mutlak koordinat sistemi sınırlayıcı kutu göre değil. Değerleri, doğrudan yerel uzayda yorumlanır.  
  
 Ek örnekler için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973). Gradyan ve diğer fırça türleri hakkında daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
