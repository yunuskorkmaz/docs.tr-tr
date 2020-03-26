---
title: 'Nasıl yapılır: Bir Öğeyi Çevirme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: addff0e22fb3f27ea924887809c0635aeb3ad67d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111978"
---
# <a name="how-to-translate-an-element"></a>Nasıl yapılır: Bir Öğeyi Çevirme
Bu örnek, bir öğeyi kullanarak nasıl <xref:System.Windows.Media.TranslateTransform>çevrilecek (taşınır) gösterir.  
  
 Sınıf, <xref:System.Windows.Media.TranslateTransform> özellikle mutlak konumlandırmayı desteklemeyen panellerin içindeki öğeleri taşımak için kullanışlıdır. Örneğin, bir öğenin <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine a uygulayarak, bir <xref:System.Windows.Controls.StackPanel> öğeyi <xref:System.Windows.Controls.DockPanel>veya .  
  
 Öğeyi <xref:System.Windows.Media.TranslateTransform.X%2A> x <xref:System.Windows.Media.TranslateTransform> ekseni boyunca taşımak için pikselolarak miktarı belirtmek için öğenin özelliğini kullanın. Öğeyi <xref:System.Windows.Media.TranslateTransform.Y%2A> y ekseni boyunca taşımak için piksellerde miktarı belirtmek için özelliği kullanın. Son olarak, <xref:System.Windows.Media.TranslateTransform> öğenin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygulayın.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.TranslateTransform> bir öğeyi 50 piksel sağa ve 50 piksel aşağıya taşımak için a kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Tam örnek için [2B Dönüşümler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dönüşümlere Genel Bakış](transforms-overview.md)
