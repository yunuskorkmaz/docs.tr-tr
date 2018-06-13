---
title: 'Nasıl yapılır: Saydam veya Yarı Saydam UIElement Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 7bf79848edb84a5bd93d1196fbe0b3196d159ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545317"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Nasıl yapılır: Saydam veya Yarı Saydam UIElement Oluşturma
Bu örnek nasıl yapılacağını gösteren bir <xref:System.Windows.UIElement> saydam veya yarı saydam. Saydam veya yarı saydam bir öğeyi göstermek için ayarladığınız kendi <xref:System.Windows.UIElement.Opacity%2A> özelliği. Değerini `0.0` öğenin değeri tamamen saydam yapar `1.0` öğesi tamamen opak yapar. Değerini `0.5` öğesi % 50 opak vb. yapar. Bir öğenin <xref:System.Windows.UIElement.Opacity%2A> ayarlanır `1.0` varsayılan olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.UIElement.Opacity%2A> bir düğmeye `0.25`, onu ve içeriği (Bu durumda düğmenin metni) % 25 donuk yapma.  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Bir öğenin içeriğini kendi varsa <xref:System.Windows.UIElement.Opacity%2A> ayarları, bu değerleri içeren öğelerle çarpılan <xref:System.Windows.UIElement.Opacity%2A>.  
  
 Aşağıdaki örnek, bir düğmenin ayarlar <xref:System.Windows.UIElement.Opacity%2A> için `0.25`ve <xref:System.Windows.UIElement.Opacity%2A> , bir <xref:System.Windows.Controls.Image> düğme içerilen denetim `0.5`. Sonuç olarak, görüntünün % 12,5 opak görünür: 0,25 * 0,5 = 0,125.  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Öğenin saydamlığını denetlemek için başka bir yol saydamlığını ayarlamaktır <xref:System.Windows.Media.Brush> öğesi boyar. Bu yaklaşım, seçmeli olarak bir öğe kısımlarının saydamlığını alter olanak tanır ve öğenin kullanmaya göre performans avantaj sağlar <xref:System.Windows.UIElement.Opacity%2A> özelliği. Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush> düğmenin boyamak için kullanılan <xref:System.Windows.Controls.Control.Background%2A> ayarlanır `0.25`. Sonuç olarak, fırça arka plan % 25 opak olur, ancak % 100 içeriğinin (düğmenin metni) kalır.  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Ayrıca bir fırça içinde tek tek renkleri geçirgenliğini denetleyebilirsiniz. Renkler ve Fırçalar hakkında daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Bir öğenin opaklık nasıl yapıldığını gösteren bir örnek için bkz [bir öğe veya fırça geçirgenliğini animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
