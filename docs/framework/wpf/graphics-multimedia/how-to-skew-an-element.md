---
title: 'Nasıl yapılır: Bir Öğeyi Eğme'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: cf770a284238826852e788e27f3b3f329ed0269f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664078"
---
# <a name="how-to-skew-an-element"></a>Nasıl yapılır: Bir Öğeyi Eğme
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.SkewTransform> bir öğeyi eğme için. Olarak da bilinen bir yamultma olan bir eğme koordinat bir Tekdüzen olmayan şekilde uzatır bir dönüşümdür. Tipik bir kullanımı, bir <xref:System.Windows.Media.SkewTransform> 2B nesneler, 3B derinliği benzetimi için olduğu.  
  
 Kullanım <xref:System.Windows.Media.SkewTransform.CenterX%2A> ve <xref:System.Windows.Media.SkewTransform.CenterY%2A> merkezi belirtmek için özellikleri noktasını <xref:System.Windows.Media.SkewTransform>.  
  
 Kullanım <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> eğme açısı x ve y ekseni belirtin ve bu eksen boyunca geçerli koordinat sistemini eğriltmek için özellikleri.  
  
 Bir eğme dönüştürmesi etkisini tahmin etmek için göz önünde bulundurun <xref:System.Windows.Media.SkewTransform.AngleX%2A> özgün koordinat sistemi x ekseni değerlerini eğriltir. Bu nedenle, bir <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30 y kaynağı üzerinden 30 derece çevirir ve değerleri x-30 derece kaynağından eğriltir. Benzer şekilde, bir <xref:System.Windows.Media.SkewTransform.AngleY%2A> şeklin y değerlerinin kaynaktan 30 derece 30 Eğer. Bu (taşıma) çevirme aynı etkiyi olmadığını unutmayın x veya y - 30 derece koordinat sistemi.  
  
 Aşağıdaki örnekte yatay eğme açısını 45 derecenin için geçerli bir <xref:System.Windows.Shapes.Rectangle> bir merkez noktadan (0,0).  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Aşağıdaki örnekte yatay eğme açısını 45 derecenin için geçerli bir <xref:System.Windows.Shapes.Rectangle> bir merkez noktadan (25,25).  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Aşağıdaki örnekte dikey eğme açısını 45 derecenin için geçerli bir <xref:System.Windows.Shapes.Rectangle> bir merkez noktadan (25,25).  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Aşağıdaki çizimde, bu örnekte kullanılan farklı farklarından gösterir.  
  
 ![SkewTransform örneği](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Gösterilen üç SkewTransform örneği  
  
 Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Nasıl Yapılır Konuları](transformations-how-to-topics.md)
