---
title: "Nasıl yapılır: Gölgeli Metin Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b031b0dce8e1fd06399ded0b6d612a23323ae837
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a>Nasıl yapılır: Gölgeli Metin Oluşturma
Bu bölümdeki örnekleri görüntülenen metin gölge efekti oluşturmayı gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Effects.DropShadowEffect> Nesne açılan çeşitli gölge efektleri oluşturmanıza imkan tanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nesneleri. Aşağıdaki örnek metne uygulanan bir gölge efekti gösterilmektedir. Bu durumda, gölge gölge rengini bulanıklıklaştırmalar anlamına gelir yumuşak gölge olmasıdır.  
  
 ![Metin gölgesinin Yumuşaklık &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Yumuşak gölgeli metin örneği  
  
 Ayarlayarak Gölge genişliğini kontrol edebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> özelliği. Değerini `4.0` 4 piksel Gölge genişliğini belirtir. Yumuşaklık kontrol edebilirsiniz veya değiştirerek bir gölge Bulanıklığı <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliği. Değerini `0.0` hiçbir bulanıklık belirtir. Aşağıdaki kod örneğinde yumuşak gölge oluşturulacağını gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Bu gölge efektleri üzerinden geçmemektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme ardışık düzeni. Sonuç olarak, ClearType bu etkilerle kullanırken devre dışı bırakıldı.  
  
 Aşağıdaki örnek metne uygulanan bir sabit gölge efekti gösterilmektedir. Bu durumda, gölge bulanık değildir.  
  
 ![Metin gölgesinin Yumuşaklık &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")  
Sabit gölgeli metin örneği  
  
 Sabit gölge ayarlayarak oluşturabileceğiniz <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliğine `0.0`, hiçbir bulanıklık olmadığını gösterir. Gölge yönünü değiştirerek denetleyebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özelliği. Bu özelliğin yönlü değerini arasında bir dereceye ayarlayın `0` ve `360`. Aşağıdaki çizimde yönlü değerlerini gösterir <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı.  
  
 ![Gölgenin DropShadow derece ayarı](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
DropShadow yönü diyagramı  
  
 Aşağıdaki kod örneğinde sabit gölge oluşturulacağını gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Bir bulanıklaştırma efekti kullanma  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnenin arkasında yerleştirilebilecek bir gölge benzeri efekti oluşturmak için kullanılır. Metne uygulanan bulanık bit eşlem Efekt metnin her yöne eşit olarak bulanıklaştırır.  
  
 Aşağıdaki örnek metne uygulanan bir bulanıklaştırma efekti gösterir.  
  
 ![Metin gölgesinin BlurBitmapEffect kullanan](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Metin Bulanıklaştırma efekti örneği  
  
 Aşağıdaki kod örneğinde bir bulanıklaştırma efekti oluşturulacağını gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Çeviri Dönüştürme kullanma  
 A <xref:System.Windows.Media.TranslateTransform> metin nesnenin arkasında yerleştirilebilecek bir gölge benzeri efekti oluşturmak için kullanılır.  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metni dengelemek için. Bu örnekte, bir gölge etkisi birincil metin altındaki metin biraz uzaklık bir kopyasını oluşturur.  
  
 ![Metin gölgesinin TranslateTransform kullanan](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")  
Dönüştürme için gölge efekti kullanarak metin örneği  
  
 Aşağıdaki kod örneğinde gölge efekti dönüşümü oluşturulacağını gösterir.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
