---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: a2225e297dbc0b5f9d49799cb34eb5539746e62e
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125791"
---
# <a name="how-to-create-text-with-a-shadow"></a>Nasıl yapılır: Gölgeli Metin Oluşturma
Bu bölümdeki örneklerde, bir gölge etkisi görüntülenen metin oluşturma işlemi gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Effects.DropShadowEffect> Nesne gölge efektleri bırakma çeşitli oluşturmanıza imkan tanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nesneleri. Aşağıdaki örnek, metne uygulanacak gölge etkisi gösterir. Bu durumda, gölge gölge rengi Bulanıklaştırma anlamına gelir. bir yazılım gölge olmasıdır.  
  
 ![Metin gölgesinin Yumuşaklık ile &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 Ayarlayarak Gölge genişliğini denetleyebilir <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> özelliği. Değerini `4.0` 4 piksel Gölge genişliğini belirtir. Yumuşaklık denetleyebilir veya değiştirerek bir gölge Bulanıklığı <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliği. Değerini `0.0` hiçbir Bulanıklaştırma gösterir. Aşağıdaki kod örneği, geçici bir gölge oluşturma gösterilmektedir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Bu gölge efektleri üzerinden geçmemektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme zinciri. Sonuç olarak, ClearType bu etkileri kullanırken devre dışı bırakıldı.  
  
 Aşağıdaki örnek, metin için uygulanan sabit gölge etkisi gösterir. Bu durumda, gölge bulanık değildir.  
  
 ![Metin gölgesinin Yumuşaklık ile &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 Sabit bir gölge ayarlayarak oluşturabileceğiniz <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliğini `0.0`, hiçbir Bulanıklaştırma kullanıldığını gösterir. Gölge yönünü değiştirerek denetleyebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özelliği. Bu özelliğin yön değeri arasında bir dereceye ayarlayın `0` ve `360`. Tek yönlü değerlerini aşağıdaki çizimde <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı.  
  
 ![Gölgenin DropShadow derece ayarı](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 Aşağıdaki kod örneği, sabit bir gölge oluşturma işlemini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Bulanıklaştırma efekt kullanma  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir. Metnin her yöne eşit olarak metne uygulanan bir bulanıklaştırma bit eşlem etkisi bulanıklaştırır.  
  
 Aşağıdaki örnek metni uygulanan bir bulanıklaştırma etkisini gösterir.  
  
 ![Metin gölgesinin BlurBitmapEffect kullanma](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 Aşağıdaki kod örneği, Bulanıklaştırma efekti oluşturma gösterilmektedir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Çeviri dönüşümü kullanma  
 A <xref:System.Windows.Media.TranslateTransform> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir.  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metin uzaklık. Bu örnekte, bir gölge etkisi birincil metin aşağıdaki metni biraz uzaklık bir kopyasını oluşturur.  
  
 ![Metin gölgesinin TranslateTransform kullanma](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 Aşağıdaki kod örneği, bir gölge etkisi dönüşümü oluşturma işlemini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
