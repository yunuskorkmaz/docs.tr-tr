---
title: 'Nasıl yapılır: Saydam veya Yarı Saydam UIElement Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370533"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Nasıl yapılır: Saydam veya Yarı Saydam UIElement Oluşturma
Bu örnek nasıl yapılacağını gösteren bir <xref:System.Windows.UIElement> saydam veya yarı saydam. Öğeyi saydam veya yarı saydam yapmak için ayarlamanız, <xref:System.Windows.UIElement.Opacity%2A> özelliği. Değerini `0.0` öğe değeri tamamen saydam yapar `1.0` öğe tamamen opak yapar. Değerini `0.5` öğe % 50 opak vb. sağlar. Bir öğenin <xref:System.Windows.UIElement.Opacity%2A> ayarlanır `1.0` varsayılan olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.UIElement.Opacity%2A> bir düğmenin `0.25`ve içeriğinin (Bu durumda düğmenin metni) % 25 donuk yapma.  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Bir öğenin içeriğini kendi varsa <xref:System.Windows.UIElement.Opacity%2A> ayarları, bu değerleri içeren öğelerle çarpılır <xref:System.Windows.UIElement.Opacity%2A>.  
  
 Aşağıdaki örnek, bir düğmenin ayarlar <xref:System.Windows.UIElement.Opacity%2A> için `0.25`ve <xref:System.Windows.UIElement.Opacity%2A> , bir <xref:System.Windows.Controls.Image> düğmede bulunan denetim `0.5`. Sonuç olarak, görüntü %12,5 donuk görünür: 0.25 * 0.5 = 0.125.  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Bir öğenin denetlemek için başka bir yolu opaklığını ayarlamaktır <xref:System.Windows.Media.Brush> , öğe boyar. Bu yaklaşım bir öğe bölümlerini opaklığını seçmeli olarak değiştirmeyi etkinleştirir ve öğenin yerine performans avantajı sağlar <xref:System.Windows.UIElement.Opacity%2A> özelliği. Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush> düğmenin boyamak için kullanılan <xref:System.Windows.Controls.Control.Background%2A> ayarlanır `0.25`. Sonuç olarak, % 25 opak fırçanın arka plan olur, ancak % 100 (düğmenin metni) içeriğini kalır.  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Ayrıca, tek tek renkler içinde bir fırça opaklığını denetleyebilirsiniz. Renkler ve Fırçalar hakkında daha fazla bilgi için bkz. [düz renkler ve gradyanlar genel bakış boyama](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Bir öğenin opaklık nasıl yapıldığını gösteren bir örnek için bkz [bir öğe veya fırça opaklığına](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
