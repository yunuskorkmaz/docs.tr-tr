---
title: 'Nasıl yapılır: Etkileşimli Olarak Saat Denetimi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951341"
---
# <a name="how-to-interactively-control-a-clock"></a>Nasıl yapılır: Etkileşimli Olarak Saat Denetimi
<xref:System.Windows.Media.Animation.Clock> Bir<xref:System.Windows.Media.Animation.ClockController> nesnenin özelliği, etkileşimli olarak başlamasını, duraklatmanızı, devam ettirmenizi, arama süresini dolduracak ve saati durdurmanıza olanak sağlar. Yalnızca bir zamanlama ağacının kök saati etkileşimli olarak denetlenebilir.  
  
> [!NOTE]
> Doğrudan saatlerle çalışmanıza gerek olmayan animasyonları etkileşimli olarak denetleyebilmeniz için başka yollar vardır: film şeritleri de kullanabilirsiniz. Görsel Taslaklar hem biçimlendirme hem de kodda desteklenir. Bir örnek için bkz. görsel taslak veya [animasyona genel bakış](animation-overview.md) [kullanarak bir özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md) .  
  
 Aşağıdaki örnekte, bir animasyon saatini etkileşimli olarak denetlemek için birkaç düğme kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animasyona Genel bakış](animation-overview.md)
