---
title: 'Nasıl yapılır: Bir Görüntüyü Küçük Resim Olarak Yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 0b5435e9b06f37dae7dc762e9035b1eca8156ca6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353394"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a>Nasıl yapılır: Bir Görüntüyü Küçük Resim Olarak Yükleme
Aşağıdaki örnekler nasıl yükleneceğini gösterir. bir <xref:System.Windows.Controls.Image> uygulama bellekten kazanacak şekilde bir küçük resim olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] görüntüyü yüklemek için gerekli bellek miktarını azaltmak için.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> görüntüyü yüklemek için gerekli bellek miktarını azaltmaya yönelik kod içinde.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntülemeye Genel Bakış](imaging-overview.md)
