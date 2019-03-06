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
ms.openlocfilehash: ec3ca16915038ebbb68df24bfd071168c346663d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372473"
---
# <a name="how-to-use-the-image-element"></a>Nasıl yapılır: Görüntü Öğesi Kullanma
Bu örnekte, görüntüleri kullanarak bir uygulamaya eklemek gösterilmektedir <xref:System.Windows.Controls.Image> öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 200 piksel genişliğinde bir görüntüsünü işlemek nasıl gösterir. Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, öznitelik söz dizimi hem özellik etiketi sözdizimi görüntünün tanımlamak için kullanılır. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md). A <xref:System.Windows.Media.Imaging.BitmapImage> özellik etiketi sözdizimi örneği için açıkça tanımlanmış ve görüntünün kaynak verileri tanımlamak için kullanılır. Ayrıca, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> , <xref:System.Windows.Media.Imaging.BitmapImage> aynı genişlikte ayarlanır <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Controls.Image>. Bu, görüntü işleme, en düşük bellek miktarını kullanılmasını sağlamak için gerçekleştirilir.  
  
> [!NOTE]
>  İşlenmiş resmin boyutu belirtmek istiyorsanız, genel olarak, yalnızca belirtin <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> ikisini birden belirtmeyin. Yalnızca birini belirtirseniz, görüntünün en boy oranı korunur. Aksi takdirde, resim, beklenmedik bir şekilde esnetilen ya da karışmış görünebilir. Görüntüyü denetlemek için davranış uzatma, kullanın <xref:System.Windows.Controls.Image.Stretch%2A> ve <xref:System.Windows.Controls.Image.StretchDirection%2A> özellikleri.  
  
> [!NOTE]
>  Belirttiğinizde görüntü boyutu ile <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A>, ya da ayarlamalısınız <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> veya <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> da aynı boyuta için.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Özelliği, görüntü öğesi doldurmak için resim kaynağını nasıl uzatılacağını belirler. Daha fazla bilgi için <xref:System.Windows.Media.Stretch> sabit listesi.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kodu kullanarak 200 piksel bir görüntüsünü işlemek nasıl gösterir.  
  
> [!NOTE]
>  Ayarı <xref:System.Windows.Media.Imaging.BitmapImage> özellikleri Bitti, içinde bir <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> blok.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntülemeye Genel Bakış](../graphics-multimedia/imaging-overview.md)
