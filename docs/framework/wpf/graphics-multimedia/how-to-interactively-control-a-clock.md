---
title: "Nasıl yapılır: Etkileşimli Olarak Saat Denetimi"
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
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24a5154607bf535cbf995705332092bb86ca02e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-interactively-control-a-clock"></a>Nasıl yapılır: Etkileşimli Olarak Saat Denetimi
A <xref:System.Windows.Media.Animation.Clock> nesnenin <xref:System.Windows.Media.Animation.ClockController> özelliği, etkileşimli olarak başlatmak, duraklatma, sürdürme, arama, dolgu süresinin ilerletme ve durdurun saati olanak tanır. Yalnızca kök saati zamanlama ağacının etkileşimli olarak denetlenebilir.  
  
> [!NOTE]
>  Etkileşimli olarak doğrudan saatlerle çalışmayı gerektirmeyen denetim animasyonlarına diğer yolu vardır: film şeritleri de kullanabilirsiniz. Film şeritleri biçimlendirme ve kodun içinde desteklenir. Bir örnek için bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) veya [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Aşağıdaki örnekte, birçok düğme etkileşimli olarak animasyon saatini denetlemek için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
