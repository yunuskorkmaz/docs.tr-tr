---
title: "Nasıl yapılır: UIElement'i Yatay veya Dikey Olarak Çevirme"
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 6b3da322493d17e4f8e36a35b9a0e40fdc9dc685
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215527"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Nasıl yapılır: UIElement'i Yatay veya Dikey Olarak Çevirme
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.ScaleTransform> ters çevirmek için bir <xref:System.Windows.UIElement> yatay veya dikey. Bu örnekte, bir <xref:System.Windows.Controls.Button> denetimi (bir tür <xref:System.Windows.UIElement>) uygulayarak çevrilmiş bir <xref:System.Windows.Media.ScaleTransform> için kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Düğme ters çevirmek için aşağıda gösterilmiştir.  
  
 ![Hiçbir dönüştürme bir düğmeyle](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
Çevrilecek UIElement  
  
 Aşağıdaki düğmeyi oluşturan kodu gösterir.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Örnek  
 Düğmenin yatay olarak çevir için oluşturma bir <xref:System.Windows.Media.ScaleTransform> ve kendi <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> özelliğini-1. Uygulama <xref:System.Windows.Media.ScaleTransform> düğmenin <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Bir düğme yatay hakkında çevrilmiş &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
ScaleTransform uyguladıktan sonra düğmesi  
  
## <a name="example"></a>Örnek  
 Önceki gösterimden görebileceğiniz gibi düğme çevrilmiş, ancak ayrıca taşındı. Sol üst köşesinden düğme çevrilmiş olmasıdır. Düğmeyi yerinde ters çevirmek için uygulamak istediğiniz <xref:System.Windows.Media.ScaleTransform> kendi Merkezi'ne köşe değil. Uygulama için kolay bir yol <xref:System.Windows.Media.ScaleTransform> düğmelere merkezi düğmenin ayarlamaktır <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 0.5 özelliğini 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Bir düğme çevrilmiş yatay ortasından](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
Düğme 0.5 RenderTransformOrigin'i 0,5  
  
## <a name="example"></a>Örnek  
 Düğmeyi Dikeyde ters çevirmek için ayarlanmış <xref:System.Windows.Media.ScaleTransform> nesnenin <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> özelliği yerine kendi <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> özelliği.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Bir düğme çevrilmiş dikey ortasından](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
Dikey olarak çevrilen düğmesi  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dönüşümlere Genel Bakış](../graphics-multimedia/transforms-overview.md)
