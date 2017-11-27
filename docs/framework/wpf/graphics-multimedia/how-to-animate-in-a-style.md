---
title: "Nasıl yapılır: Bir Stile Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10cd243c633e7a7e458d2026fc5e3d91d2996427
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-in-a-style"></a>Nasıl yapılır: Bir Stile Animasyon Ekleme
Bu örnek, stil içindeki özelliklere animasyon gösterilmektedir. Stil içinde animasyon eklerken, yalnızca stili tanımlandığı çerçeve öğesi doğrudan hedeflenebilir. Freezable nesne hedeflemek için "aşağı stilde öğe özelliğinden nokta gerekir".  
  
 Aşağıdaki örnekte, birkaç animasyon stil içinde tanımlanır ve uygulanan bir <xref:System.Windows.Controls.Button>. Kullanıcı fare düğmesini taşındığında, opak görünümden kısmen saydam ve geri belirerek, tekrar. Kullanıcının fare düğmesini devre dışı geçtiğinde, tamamen opak olur. Düğmesine tıklandığında, arka plan rengi beyaz ve yeniden turuncu değiştirir. Çünkü <xref:System.Windows.Media.SolidColorBrush> boyamak için kullanılan düğme doğrudan hedefleyemez, düğmenin noktalanarak erişilir <xref:System.Windows.Controls.Control.Background%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Stil içinde animasyon eklerken, yoksa hedef nesneler için mümkün olduğunu unutmayın. Örneğin, stilinize kullandığını varsayın bir <xref:System.Windows.Media.SolidColorBrush> düğmenin arka plan özelliği ayarlanmış, ancak bir stil noktada için geçersiz kılınır ve düğmenin arka planı ile ayarlanmış bir <xref:System.Windows.Media.LinearGradientBrush>.  Animasyon çalışılırken <xref:System.Windows.Media.SolidColorBrush> bir özel durum; throw olmaz animasyon sessizce başarısız olur.  
  
 Sözdizimi hedefleyen film şeridi hakkında daha fazla bilgi için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Animasyon hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Stilleri hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).
