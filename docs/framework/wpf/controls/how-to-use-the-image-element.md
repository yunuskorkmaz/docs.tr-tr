---
title: 'Nasıl yapılır: Görüntü Öğesi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 164eee7c10d9e388c6e6ee695af479ca2d6974b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958321"
---
# <a name="how-to-use-the-image-element"></a>Nasıl yapılır: Görüntü Öğesi Kullanma
Bu örnek, <xref:System.Windows.Controls.Image> öğesini kullanarak bir uygulamaya görüntülerin nasıl ekleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir görüntünün 200 piksel genişliğinde nasıl işleneceğini gösterir. Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekte, görüntüyü tanımlamak için hem öznitelik sözdizimi hem de özellik etiketi sözdizimi kullanılır. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md). <xref:System.Windows.Media.Imaging.BitmapImage> , Görüntünün kaynak verilerini tanımlamak için kullanılır ve özellik etiketi sözdizimi örneği için açıkça tanımlanmıştır. Ayrıca, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.FrameworkElement.Width%2A> öğesinin ' ı ile aynı <xref:System.Windows.Controls.Image>genişliğe ayarlanır. <xref:System.Windows.Media.Imaging.BitmapImage> Bu, görüntüyü işlemek için en az bellek miktarının kullanıldığından emin olmak için yapılır.  
  
> [!NOTE]
> Genel olarak, işlenmiş bir görüntünün boyutunu belirtmek istiyorsanız, her ikisini de yalnızca <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> veya ' ı belirtin. Yalnızca bir tane belirtirseniz, görüntünün en boy oranı korunur. Aksi takdirde, görüntü beklenmedik şekilde uzatılmış veya çarpıtılmış görünebilir. Görüntünün uzatma davranışını denetlemek için <xref:System.Windows.Controls.Image.Stretch%2A> ve <xref:System.Windows.Controls.Image.StretchDirection%2A> özelliklerini kullanın.  
  
> [!NOTE]
> Ya <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> da ile bir görüntünün boyutunu belirttiğinizde, ya da aynı boyuta göre de ayarlamanız gerekir. <xref:System.Windows.FrameworkElement.Height%2A>  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Özelliği, görüntü kaynağının görüntü öğesini doldurmak için nasıl uzatılacağını belirler. Daha fazla bilgi için bkz <xref:System.Windows.Media.Stretch> . sabit listesi.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kod kullanarak bir görüntünün 200 piksel genelinde nasıl işleneceğini gösterir.  
  
> [!NOTE]
> Ayar <xref:System.Windows.Media.Imaging.BitmapImage> özellikleri bir <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloğu içinde yapılmalıdır.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntülemeye Genel Bakış](../graphics-multimedia/imaging-overview.md)
