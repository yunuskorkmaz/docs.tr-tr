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
ms.openlocfilehash: 11481533af7b3ad75b571f9f97251c123e0af1b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555918"
---
# <a name="how-to-use-the-image-element"></a>Nasıl yapılır: Görüntü Öğesi Kullanma
Bu örnek görüntüleri kullanarak, bir uygulamada dahil etmek nasıl gösterir <xref:System.Windows.Controls.Image> öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir resmin 200 piksel genişliğinde nasıl işleneceğini gösterir. Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, öznitelik sözdizimi ve özellik etiketi sözdizimi görüntü tanımlamak için kullanılır. Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). A <xref:System.Windows.Media.Imaging.BitmapImage> görüntünün kaynak verileri tanımlamak için kullanılır ve özellik etiketi sözdizimi örneği için açıkça tanımlanır. Ayrıca, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> , <xref:System.Windows.Media.Imaging.BitmapImage> aynı genişliğe ayarlanır <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Controls.Image>. Bu görüntü işleme, en düşük bellek miktarını kullanılmasını sağlamak amacıyla gerçekleştirilir.  
  
> [!NOTE]
>  İşlenmiş resmin boyutunu belirtmek istiyorsanız, genel olarak, yalnızca belirtin <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> ikisini birden belirtmeyin. Yalnızca birini belirtirseniz, resmin en boy oranı korunur. Aksi takdirde, resim, beklenmedik bir şekilde uzamış ya da çarpık görünebilir. Görüntü denetlemek için davranış uzatma, kullanın <xref:System.Windows.Controls.Image.Stretch%2A> ve <xref:System.Windows.Controls.Image.StretchDirection%2A> özellikleri.  
  
> [!NOTE]
>  Belirttiğinizde görüntüsünün boyutu ile ya da <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A>, ya da ayarlamalısınız <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> veya <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> aynı boyuta için.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Özelliği, görüntü kaynağı bir görüntü öğesi doldurmak için nasıl genişletilir belirler. Daha fazla bilgi için bkz: <xref:System.Windows.Media.Stretch> numaralandırması.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir resmin 200 piksel genişliğinde kod kullanarak nasıl işleneceğini gösterir.  
  
> [!NOTE]
>  Ayarı <xref:System.Windows.Media.Imaging.BitmapImage> özellikleri Bitti, içinde bir <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloğu.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntülemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
