---
title: "Nasıl yapılır: Çizime GuidelineSet Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf689f8a7c475dbdda416297e28118d43bfdbff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Nasıl yapılır: Çizime GuidelineSet Uygulama
Bu örnek nasıl uygulanacağını gösterir bir <xref:System.Windows.Media.GuidelineSet> için bir <xref:System.Windows.Media.DrawingGroup>.  
  
 <xref:System.Windows.Media.DrawingGroup> Sınıftır türü <xref:System.Windows.Media.Drawing> olan bir <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> özelliği. Uygulanacak bir <xref:System.Windows.Media.GuidelineSet> başka türde <xref:System.Windows.Media.Drawing>, ekleyebilmek için bir <xref:System.Windows.Media.DrawingGroup> ve ardından uygulama <xref:System.Windows.Media.GuidelineSet> için <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Media.DrawingGroup> tek fark neredeyse aynı; nesneleri: ikinci <xref:System.Windows.Media.DrawingGroup> sahip bir <xref:System.Windows.Media.GuidelineSet> ve ilk desteklemez.  
  
 Aşağıdaki çizimde örnek çıktısını gösterir. İşleme fark nedeniyle arasında iki <xref:System.Windows.Media.DrawingGroup> nesnedir nedenle hafif, çizimlerin bölümleri genişletilir.  
  
 ![İle ve GuidelineSet olmadan DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
