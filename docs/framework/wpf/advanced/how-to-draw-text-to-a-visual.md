---
title: 'Nasıl yapılır: Görsele Metin Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: bc7a4f989137ec2b021d27a6e112ff1aebd99d07
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523249"
---
# <a name="how-to-draw-text-to-a-visual"></a>Nasıl yapılır: Görsele Metin Çizme
Aşağıdaki örnek için metin Çiz gösterilmiştir bir <xref:System.Windows.Media.DrawingVisual> kullanarak bir <xref:System.Windows.Media.DrawingContext> nesne. Çizim Bağlamı çağırarak döndürülür <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> yöntemi bir <xref:System.Windows.Media.DrawingVisual> nesne. Grafikler ve metin çizim bağlamına çizebilirsiniz.  
  
 Metin çizme bağlamına çizmek için <xref:System.Windows.Media.DrawingContext.DrawText%2A> yöntemi bir <xref:System.Windows.Media.DrawingContext> nesne. Çizim bağlamına çizim içeriği tamamladığınızda, çağrı <xref:System.Windows.Media.DrawingContext.Close%2A> çizim bağlamı kapatmak ve içeriği kalıcı hale getirmek için yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Kendisinden önceki kod örneğinde çıkarılan tam kod örneği için bkz [isabet sınaması örneği kullanarak Test isabet](https://go.microsoft.com/fwlink/?LinkID=159994).
