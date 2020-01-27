---
title: Bir stille animasyon ekleme
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 0b29648bf15f0046adcdee610f9565f7deb24972
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744886"
---
# <a name="how-to-animate-in-a-style"></a>Bir stille animasyon ekleme

Bu örnek, bir stil içindeki özelliklerin nasıl hareketlendirileceğini gösterir. Bir stil içinde animasyon eklerken, yalnızca stilin tanımlandığı Framework öğesi doğrudan hedeflenebilir. Freezable nesnesini hedeflemek için, stilli bir öğenin özelliğinden "nokta aşağı" yazmanız gerekir.

Aşağıdaki örnekte, bir stil içinde birkaç animasyon tanımlanmıştır ve bir <xref:System.Windows.Controls.Button>uygulanır. Kullanıcı fareyi düğmenin üzerine taşıdığında, opak ve kısmen yarı saydam, tekrar tekrar tekrar tekrar olur. Kullanıcı fareyi düğme dışına taşıdıkça tamamen opak hale gelir. Düğmeye tıklandığında, arka plan rengi turuncu 'dan beyaza ve yeniden geri değişir. Düğmeyi boyamak için kullanılan <xref:System.Windows.Media.SolidColorBrush> doğrudan hedeflenemediği için düğmenin <xref:System.Windows.Controls.Control.Background%2A> özelliğinden aşağı doğru biçimlendirme tarafından erişilir.

## <a name="example"></a>Örnek

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Bir stil içinde animasyon uyguladığınızda, mevcut olmayan nesneleri hedeflemek mümkün olduğunu unutmayın. Örneğin, bir düğmenin arkaplan özelliğini ayarlamak için stilinizin <xref:System.Windows.Media.SolidColorBrush> kullandığını varsayalım, ancak bir noktada stil geçersiz kılınır ve düğmenin arka planı bir <xref:System.Windows.Media.LinearGradientBrush>ile ayarlanır.  <xref:System.Windows.Media.SolidColorBrush> hareketlendirme girişimi bir özel durum oluşturmaz; animasyon sessizce başarısız olur.

Görsel taslak hedefleme sözdizimi hakkında daha fazla bilgi için bkz. görsel taslaklara [genel bakış](storyboards-overview.md). Animasyon hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md). Stiller hakkında daha fazla bilgi için bkz. [Stil ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.
