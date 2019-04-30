---
title: 'Nasıl yapılır: Çizime GuidelineSet Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 134236c5beca806b747d45f20764cc82ddd8a4e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699061"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Nasıl yapılır: Çizime GuidelineSet Uygulama
Bu örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.GuidelineSet> için bir <xref:System.Windows.Media.DrawingGroup>.  
  
 <xref:System.Windows.Media.DrawingGroup> Sınıfı, yalnızca türü <xref:System.Windows.Media.Drawing> olan bir <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> özelliği. Uygulanacak bir <xref:System.Windows.Media.GuidelineSet> başka türde <xref:System.Windows.Media.Drawing>, ekleyebilmek için bir <xref:System.Windows.Media.DrawingGroup> ve daha sonra uygulamanızı <xref:System.Windows.Media.GuidelineSet> için <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki oluşturur <xref:System.Windows.Media.DrawingGroup> tek fark neredeyse aynı; olan nesneler: ikinci <xref:System.Windows.Media.DrawingGroup> sahip bir <xref:System.Windows.Media.GuidelineSet> ve ilk desteklemez.  
  
 Örneğin çıktısında aşağıda gösterilmiştir. İşleme çünkü arasında iki <xref:System.Windows.Media.DrawingGroup> nesneleri, küçük, çizimler bölümlerini genişletilir.  
  
 ![DrawingGroup GuidelineSet olmadan ve](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
