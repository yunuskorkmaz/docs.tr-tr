---
title: 'Nasıl yapılır: Bir Öğe veya Fırça Opaklığına Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 2f18861eb18f81b631245d1d933b7acb1b3e0e42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950508"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Nasıl yapılır: Bir Öğe veya Fırça Opaklığına Animasyon Ekleme
Bir çerçeve öğesini soluklaştırmak ve görünümün dışında bırakmak için, <xref:System.Windows.UIElement.Opacity%2A> özelliğine animasyon ekleyebilir ya da boyamak için kullanılan <xref:System.Windows.Media.Brush> (ya da <xref:System.Windows.Media.Brush.Opacity%2A> fırçaların) özelliğine animasyon uygulayabilirsiniz. Öğenin Opaklığına Animasyon eklemek, ve alt öğelerini ekranda soluklaştırır ve görünümden çıkar, ancak öğeyi boyamak için kullanılan fırçayı hareketlendirmek, öğenin hangi bölümünün soldurmasına ilişkin daha seçmeli olmanızı sağlar. Örneğin, bir düğmenin arka planını boyamak için kullanılan bir fırçanın opaklığını canlandırabilirsiniz. Bu, düğmenin arka planının görünüm altına alınmasına ve dışına çıkmamasına neden olur, böylece metin tamamen opak olur.  
  
> [!NOTE]
> Bir öğesinin <xref:System.Windows.Media.Brush.Opacity%2A> canlandırmasına <xref:System.Windows.Media.Brush> , bir öğe <xref:System.Windows.UIElement.Opacity%2A> özelliğinin canlandırmasına ilişkin performans avantajları sağlar.  
  
 Aşağıdaki örnekte, iki düğme canlandırılır ve görünümün dışına çıkar. İlki <xref:System.Windows.Controls.Button> geçirgenliği, beş saniyelik bir `0.0` <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ile arasında `1.0` canlandırılır. İkinci düğme de hareketlendirilir, ancak tüm düğmenin geçirgenliği yerine animasyon eklemek için <xref:System.Windows.Controls.Control.Background%2A> kullanılan SolidColorBrush geçirgenliği. Örnek çalıştırıldığında, ilk düğme tamamen görünümden kaybolur ve ekrandan çıkar, ancak yalnızca ikinci düğmenin arka planı görünümden kaybolur ve ekrandan çıkar. Metni ve kenarlığı tamamen donuk kalır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Kod bu örnekte atlandı. Tam örnek ayrıca <xref:System.Windows.Media.Color> <xref:System.Windows.Media.LinearGradientBrush>içindeki içindeki opaklığın nasıl hareketlendirileceğini gösterir.  Tam örnek için, [bir öğe örneğinin Opaklığına Animasyon Ekleme](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation)bölümüne bakın.
