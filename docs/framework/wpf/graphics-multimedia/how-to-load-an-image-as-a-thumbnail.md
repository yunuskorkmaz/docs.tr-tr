---
title: "Nasıl yapılır: Bir Görüntüyü Küçük Resim Olarak Yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: adcbd5fb82ce9ae89ac59db5aeb7f384f8cc1fc7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a>Nasıl yapılır: Bir Görüntüyü Küçük Resim Olarak Yükleme
Aşağıdaki örnekler nasıl yükleneceğini bir <xref:System.Windows.Controls.Image> uygulama belleğini korumak için bir küçük resim olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] resmi yüklemek için gerekli bellek miktarını azaltmak için.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> resmi yüklemek için gerekli bellek miktarını azaltmak için kod.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntü oluşturmaya genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
