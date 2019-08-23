---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960437"
---
# <a name="how-to-create-text-with-a-shadow"></a>Nasıl yapılır: Gölgeli Metin Oluşturma
Bu bölümdeki örneklerde, görüntülenecek metin için bir gölge efektinin nasıl oluşturulacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Nesnesi <xref:System.Windows.Media.Effects.DropShadowEffect> , nesneler için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çeşitli gölge efektler oluşturmanızı sağlar. Aşağıdaki örnek, metne uygulanan bir gölge efekti gösterir. Bu durumda, gölge bir gölgedir, bu da gölge rengin bulanıklaştırmasıdır.  
  
 ![Soflük &#61; 0,25 ile metin gölgesi](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> Özelliği ayarlayarak bir gölgenin genişliğini kontrol edebilirsiniz. Değeri 4 piksellik `4.0` bir gölge genişliği gösterir. <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliği değiştirerek, bir gölgenin yumuşaklığını veya bulanıklaştırarak denetim yapabilirsiniz. Değeri, `0.0` bulanıklık olmadığını gösterir. Aşağıdaki kod örneği, nasıl yumuşak bir gölge oluşturulacağını göstermektedir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Bu gölge etkileri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme ardışık düzeninde ilerleyemez. Sonuç olarak, bu efektler kullanılırken ClearType devre dışıdır.  
  
 Aşağıdaki örnekte, metne uygulanan bir sabit gölge efekti gösterilmektedir. Bu durumda, gölge bulanık değildir.  
  
 ![Soflük &#61; 0 ile metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> Özelliğini olarak`0.0`ayarlayarak sabit bir gölge oluşturabilirsiniz. Bu, bir bulanıklık kullanılmadığını gösterir. <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> Özelliği değiştirerek Gölgenin yönünü kontrol edebilirsiniz. Bu özelliğin yönlü değerini ve `0` `360`arasında bir dereceye ayarlayın. Aşağıdaki çizim, <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarının yönlü değerlerini gösterir.  
  
 ![Gölgenin DropShadow derecesi ayarı](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 Aşağıdaki kod örneği, sabit gölge oluşturmayı gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Bulanıklaştırma efekti kullanma  
 Bir <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesinin arkasına yerleştirilebilecek bir gölge benzeri efekt oluşturmak için kullanılabilir. Metne uygulanan bir bulanıklaştırma bit eşlem efekti, metni her yönden eşit şekilde bulanıklaştırır.  
  
 Aşağıdaki örnek, metne uygulanan bir bulanıklaştırma efektini gösterir.  
  
 ![Bir BlurBitmapEffect kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 Aşağıdaki kod örneği, bir bulanıklaştırma efektinin nasıl oluşturulacağını göstermektedir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Çeviri dönüştürmesi kullanma  
 Bir <xref:System.Windows.Media.TranslateTransform> metin nesnesinin arkasına yerleştirilebilecek bir gölge benzeri efekt oluşturmak için kullanılabilir.  
  
 Aşağıdaki kod örneği, metin kaydırmak <xref:System.Windows.Media.TranslateTransform> için bir kullanır. Bu örnekte, birincil metnin altındaki metnin biraz bir konum kopyası bir gölge efekti oluşturur.  
  
 ![TranslateTransform kullanarak metin gölgesi](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 Aşağıdaki kod örneği, bir gölge efekti için dönüşümün nasıl oluşturulacağını göstermektedir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
