---
title: Nasıl (WPF) bir stile animasyon ekleme
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: a455bbfb9defbcf83f7e490f60031917a3b41779
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540063"
---
# <a name="how-to-animate-in-a-style"></a>Nasıl bir stile animasyon ekleme

Bu örnek, bir stil içinde özelliklerine animasyon gösterilmektedir. Bir stil içinde animasyon zaman stili tanımlandığı framework öğesi doğrudan hedefleyebilir. Freezable nesne hedeflemek için "aşağı bir stil uygulanmış öğesi özellikten nokta gerekir".

Aşağıdaki örnekte, birkaç animasyon bir stil içinde tanımlanan ve uygulanan bir <xref:System.Windows.Controls.Button>. Kullanıcı düğmenin üzerine fareyi hareket ettirdiğinde, donuk kısmen saydam ve geri belirerek, tekrar. Kullanıcı fareyi düğmeden hareket ettirdiğinde tamamen opak olur. Düğme tıklandığında, beyaz ve yeniden turuncudan arka plan rengini değiştirir. Çünkü <xref:System.Windows.Media.SolidColorBrush> boyamak için kullanılan düğme doğrudan hedeflenemez, düğmenin noktalanarak erişilir <xref:System.Windows.Controls.Control.Background%2A> özelliği.

## <a name="example"></a>Örnek

[!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Stil içinde animasyon zaman, mevcut olmayan hedef nesnelere mümkün olduğunu unutmayın. Örneğin, stili kullanan varsayalım bir <xref:System.Windows.Media.SolidColorBrush> düğmenin arka plan ile ayarlanır ve bir düğmenin arka plan özelliği ayarlandı, ancak bir noktada stili için geçersiz bir <xref:System.Windows.Media.LinearGradientBrush>.  Animasyon çalışılırken <xref:System.Windows.Media.SolidColorBrush> ; özel durum olmaz animasyon sessizce başarısız olur.

Söz dizimi hedefleyen görsel taslak hakkında daha fazla bilgi için bkz: [görsel taslaklara genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Animasyon hakkında daha fazla bilgi için bkz. [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Stilleri hakkında daha fazla bilgi için bkz. [stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md).
