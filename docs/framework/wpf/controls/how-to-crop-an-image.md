---
title: 'Nasıl yapılır: Görüntü Kırpma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: f4c1a735ac102b3f6d81b5253bc15a5d1893075c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366809"
---
# <a name="how-to-crop-an-image"></a>Nasıl yapılır: Görüntü Kırpma
Bu örnek gösterir kullanarak bir görüntü kırpma <xref:System.Windows.Media.Imaging.CroppedBitmap>.  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> öncelikle bir resim kırpılmış bir sürümünü kodlarken çıkış bir dosyaya kaydetmek için kullanılır. Görüntüleme amaçları için bkz. görüntü kırpma için [nasıl yapılır: Kırpma bölgesini oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90)) konu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekleri içinde kullanılan kaynakları tanımlar.  
  
 [!code-xaml[imageelementexample#CroppedXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 Aşağıdaki örnek, kullanarak bir görüntü oluşturur. bir <xref:System.Windows.Media.Imaging.CroppedBitmap> kaynağı olarak.  
  
 [!code-xaml[imageelementexample#CroppedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> De başka bir kaynak olarak kullanılabilir <xref:System.Windows.Media.Imaging.CroppedBitmap>, kırpma zincirleme. Unutmayın <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> kaynak bit eşlem ve olmayan ilk resim kırpılmış göreli olan değerleri kullanır.  
  
 [!code-xaml[imageelementexample#CroppedXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Kırpma bölgesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))
