---
title: 'Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913912"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma
Bu örnek, bir <xref:System.Windows.Media.MatrixTransform> <xref:System.Windows.Controls.Button>öğesinin konumunu, uzatılmasına ve eğriliğini çevirmek (taşımak) için nasıl kullanılacağını gösterir.  
  
> [!NOTE]
> <xref:System.Windows.Media.RotateTransform> ,,<xref:System.Windows.Media.SkewTransform>Veya sınıfları<xref:System.Windows.Media.TranslateTransform> tarafından sağlanmayan<xref:System.Windows.Media.ScaleTransform>özel dönüştürmeler oluşturmak için sınıfını kullanın. <xref:System.Windows.Media.MatrixTransform>  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Nasıl Yapılır Konuları](transformations-how-to-topics.md)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)
