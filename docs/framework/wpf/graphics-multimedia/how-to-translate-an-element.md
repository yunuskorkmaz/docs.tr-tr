---
title: 'Nasıl yapılır: Bir Öğeyi Çevirme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: ba6bda09a4ee189cdd1a32eed8f65b32d1a9abe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187314"
---
# <a name="how-to-translate-an-element"></a>Nasıl yapılır: Bir Öğeyi Çevirme
Bu örnek, bir öğeyi kullanarak nasıl <xref:System.Windows.Media.TranslateTransform>çevrilecek (taşınır) gösterir.  
  
 Sınıf, <xref:System.Windows.Media.TranslateTransform> özellikle mutlak konumlandırmayı desteklemeyen panellerin içindeki öğeleri taşımak için kullanışlıdır. Örneğin, bir öğenin <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine a uygulayarak, bir <xref:System.Windows.Controls.StackPanel> öğeyi <xref:System.Windows.Controls.DockPanel>veya .  
  
 Öğeyi <xref:System.Windows.Media.TranslateTransform.X%2A> x <xref:System.Windows.Media.TranslateTransform> ekseni boyunca taşımak için pikselolarak miktarı belirtmek için öğenin özelliğini kullanın. Öğeyi <xref:System.Windows.Media.TranslateTransform.Y%2A> y ekseni boyunca taşımak için piksellerde miktarı belirtmek için özelliği kullanın. Son olarak, <xref:System.Windows.Media.TranslateTransform> öğenin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygulayın.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.TranslateTransform> bir öğeyi 50 piksel sağa ve 50 piksel aşağıya taşımak için a kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Numunenin tamamı için [2-B Dönüşüm Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dönüşümlere Genel Bakış](transforms-overview.md)
