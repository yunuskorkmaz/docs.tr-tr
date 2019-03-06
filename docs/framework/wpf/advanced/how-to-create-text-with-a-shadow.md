---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 4d200aa980e8f2e6d22291669dfb07db54a5f0c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370689"
---
# <a name="how-to-create-text-with-a-shadow"></a>Nasıl yapılır: Gölgeli Metin Oluşturma
Bu bölümdeki örneklerde, bir gölge etkisi görüntülenen metin oluşturma işlemi gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Effects.DropShadowEffect> Nesne gölge efektleri bırakma çeşitli oluşturmanıza imkan tanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nesneleri. Aşağıdaki örnek, metne uygulanacak gölge etkisi gösterir. Bu durumda, gölge gölge rengi Bulanıklaştırma anlamına gelir. bir yazılım gölge olmasıdır.  
  
 ![Metin gölgesinin Yumuşaklık ile &#61; 0,25](./media/shadowtext01.jpg "ShadowText01")  
Yazılım gölgeli metin örneği  
  
 Ayarlayarak Gölge genişliğini denetleyebilir <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> özelliği. Değerini `4.0` 4 piksel Gölge genişliğini belirtir. Yumuşaklık denetleyebilir veya değiştirerek bir gölge Bulanıklığı <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliği. Değerini `0.0` hiçbir Bulanıklaştırma gösterir. Aşağıdaki kod örneği, geçici bir gölge oluşturma gösterilmektedir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Bu gölge efektleri üzerinden geçmemektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme zinciri. Sonuç olarak, ClearType bu etkileri kullanırken devre dışı bırakıldı.  
  
 Aşağıdaki örnek, metin için uygulanan sabit gölge etkisi gösterir. Bu durumda, gölge bulanık değildir.  
  
 ![Metin gölgesinin Yumuşaklık ile &#61; 0](./media/shadowtext02.jpg "ShadowText02")  
Sabit gölgeli metin örneği  
  
 Sabit bir gölge ayarlayarak oluşturabileceğiniz <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliğini `0.0`, hiçbir Bulanıklaştırma kullanıldığını gösterir. Gölge yönünü değiştirerek denetleyebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özelliği. Bu özelliğin yön değeri arasında bir dereceye ayarlayın `0` ve `360`. Tek yönlü değerlerini aşağıdaki çizimde <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı.  
  
 ![Gölgenin DropShadow derece ayarı](./media/shadowtext08.png "ShadowText08")  
DropShadow yönü diyagramı  
  
 Aşağıdaki kod örneği, sabit bir gölge oluşturma işlemini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Bulanıklaştırma efekt kullanma  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir. Metnin her yöne eşit olarak metne uygulanan bir bulanıklaştırma bit eşlem etkisi bulanıklaştırır.  
  
 Aşağıdaki örnek metni uygulanan bir bulanıklaştırma etkisini gösterir.  
  
 ![Metin gölgesinin BlurBitmapEffect kullanarak](./media/shadowtext06.jpg "ShadowText06")  
Bulanıklaştırma etkisi olan metin örneği  
  
 Aşağıdaki kod örneği, Bulanıklaştırma efekti oluşturma gösterilmektedir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Çeviri dönüşümü kullanma  
 A <xref:System.Windows.Media.TranslateTransform> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir.  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metin uzaklık. Bu örnekte, bir gölge etkisi birincil metin aşağıdaki metni biraz uzaklık bir kopyasını oluşturur.  
  
 ![Metin gölgesinin TranslateTransform kullanan](./media/shadowtext07.jpg "ShadowText07")  
Metin dönüştürme için gölge etkisi kullanarak örneği  
  
 Aşağıdaki kod örneği, bir gölge etkisi dönüşümü oluşturma işlemini gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
