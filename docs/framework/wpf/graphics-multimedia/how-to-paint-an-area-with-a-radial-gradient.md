---
title: "Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55b707e4738a77a8fb093071ef6f5105b2200c16
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.RadialGradientBrush> Radyal gradyan ile bir alanı boyamak için sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.RadialGradientBrush> yeşile mavi ve kırmızı sarı geçiş Radyal gradyan ile bir dikdörtgen boyamak için.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Aşağıdaki çizimde, önceki örnekten gradyanı gösterir. Vurgulanan gradyan durdurur.  
  
 ![Radyal gradyan gradyan duraklarının](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  Bu konudaki örnekler denetim noktalarını ayarlamak için varsayılan koordinat sistemi kullanır. Varsayılan koordinat sistemi göreli bir sınırlama kutusudur: 0 gösterir sınırlayıcı kutusunun yüzde 0 ve 1 sınırlayıcı kutusunun yüzde 100 gösterir. Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğinin değeri <xref:System.Windows.Media.BrushMappingMode.Absolute>. Mutlak koordinat sistemi sınırlayıcı kutu göre değil. Değerleri, doğrudan yerel uzayda yorumlanır.  
  
 İçin ek <xref:System.Windows.Media.RadialGradientBrush> örnekler, bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973). Gradyan ve diğer fırça türleri hakkında daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
