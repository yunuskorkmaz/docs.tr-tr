---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186844"
---
# <a name="how-to-create-text-with-a-shadow"></a>Nasıl yapılır: Gölgeli Metin Oluşturma
Bu bölümdeki örnekler, görüntülenen metin için gölge efektinin nasıl oluşturulabildiğini gösterir.  
  
## <a name="example"></a>Örnek  
 Nesne, <xref:System.Windows.Media.Effects.DropShadowEffect> nesneler için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çeşitli damla gölge efektleri oluşturmanıza olanak tanır. Aşağıdaki örnekte, metne uygulanan bir açılır gölge efekti gösterilmektedir. Bu durumda, gölge yumuşak bir gölgedir, bu da gölge renginin bulanıkolduğu anlamına gelir.  
  
 ![Yumuşaklıklı metin gölgesi 0,25 &#61;](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> Özelliği ayarlayarak gölgenin genişliğini denetleyebilirsiniz. Değeri 4 `4.0` piksel lik bir gölge genişliğini gösterir. <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliği değiştirerek gölgenin yumuşaklığını veya bulanıklığını denetleyebilirsiniz. Bir değer `0.0` bulanıklık gösterir. Aşağıdaki kod örneği, yumuşak bir gölgenin nasıl oluşturulabildiğini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Bu gölge efektleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme ardışık etki tarafından gitmez. Sonuç olarak, bu efektleri kullanırken ClearType devre dışı bırakılır.  
  
 Aşağıdaki örnek, metne uygulanan sabit bir gölge efekti gösterir. Bu durumda, gölge bulanık değildir.  
  
 ![Yumuşaklık &#61; 0 ile metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliği `0.0`, bulanıklık kullanılmadığını gösteren şekilde ayarlayarak sabit bir gölge oluşturabilirsiniz. <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> Özelliği değiştirerek gölgenin yönünü denetleyebilirsiniz. Bu özelliğin yön değerini bir `0` dereceye `360`kadar ayarlayın. Aşağıdaki resimde <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı yön değerlerini gösterir.  
  
 ![Gölgenin DropShadow derece ayarı](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 Aşağıdaki kod örneği, sabit bir gölgenin nasıl oluşturulabildiğini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Bulanıklaştırma Efekti Kullanma  
 A, <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesi arkasına yerleştirilebilir gölge benzeri bir efekt oluşturmak için kullanılabilir. Metne uygulanan bulanıklık biteşefekti efekti metni tüm yönlerde eşit olarak bulanıklaştırır.  
  
 Aşağıdaki örnekte metne uygulanan bulanıklık efekti gösterilmektedir.  
  
 ![BlurBitmapEffect kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 Aşağıdaki kod örneği, bulanıklaştırma efektinin nasıl oluşturulabildiğini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Çevirme Dönüştürme'yi Kullanma  
 A, <xref:System.Windows.Media.TranslateTransform> metin nesnesi arkasına yerleştirilebilir gölge benzeri bir efekt oluşturmak için kullanılabilir.  
  
 Aşağıdaki kod örneği, <xref:System.Windows.Media.TranslateTransform> metni dengelemek için a kullanır. Bu örnekte, birincil metnin altındaki metnin biraz ofset kopyası gölge efekti oluşturur.  
  
 ![TranslateTransform kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 Aşağıdaki kod örneği, gölge efekti için dönüşümün nasıl oluşturulabildiğini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
