---
title: 'Nasıl yapılır: Bir Öğeyi Eğme'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112030"
---
# <a name="how-to-skew-an-element"></a>Nasıl yapılır: Bir Öğeyi Eğme
Bu örnek, bir <xref:System.Windows.Media.SkewTransform> öğeyi eğriltmek için a'nın nasıl kullanılacağını gösterir. Bir eğrilik, aynı zamanda bir yama olarak bilinen, olmayan bir üniforma şekilde koordinat alanı uzanan bir dönüşümdür. A'nın <xref:System.Windows.Media.SkewTransform> tipik bir kullanımı, 2B nesnelerdeki 3B derinliği simüle etmektir.  
  
 'nin <xref:System.Windows.Media.SkewTransform.CenterX%2A> <xref:System.Windows.Media.SkewTransform.CenterY%2A> merkez noktasını belirtmek için ve özelliklerini kullanın. <xref:System.Windows.Media.SkewTransform>  
  
 X <xref:System.Windows.Media.SkewTransform.AngleX%2A> ekseni ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> y ekseninin çarpık açısını belirtmek ve bu eksenler boyunca geçerli koordinat sistemini eğriltmek için ve özellikleri kullanın.  
  
 Çarpık dönüşümün etkisini tahmin etmek için, <xref:System.Windows.Media.SkewTransform.AngleX%2A> x ekseni değerlerini özgün koordinat sistemine göre çarpıtmayı düşünün. Bu nedenle, <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30'lu bir için y ekseni menşei boyunca 30 derece döner ve x-'deki değerleri bu kaynaktan 30 derece eğritir. Aynı şekilde, <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30'dan biri şeklin y değerlerini kökenden 30 derece eğriltiyor. Bunun koordinat sistemini x veya y-'de 30 derece çevirmek (taşımak) ile aynı etkiyi yaratmadığını unutmayın.  
  
 Aşağıdaki örnek, (0,0) bir merkez noktasından <xref:System.Windows.Shapes.Rectangle> a 45 derecelik yatay bir eğrilik uygular.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Aşağıdaki örnek, (25,25) bir merkez <xref:System.Windows.Shapes.Rectangle> noktasından a için 45 derecelik yatay bir eğrilik uygular.  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Aşağıdaki örnek, (25,25) bir merkez <xref:System.Windows.Shapes.Rectangle> noktasından a için 45 derecelik dikey bir eğrilik uygular.  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Aşağıdaki resimde, bu örnekte kullanılan farklı eğrilikler gösterilmektedir.  
  
 ![SkewTransform örnekleri](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Üç SkewTransform örnekleri resimli  
  
 Tam örnek için [2B Dönüşümler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Nasıl Dır Konular](transformations-how-to-topics.md)
