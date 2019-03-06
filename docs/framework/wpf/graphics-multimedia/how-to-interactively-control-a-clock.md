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
ms.openlocfilehash: 6d3dbc8c39e63b46871b0cc88fbe8d5d51b63463
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361661"
---
# <a name="how-to-interactively-control-a-clock"></a>Nasıl yapılır: Etkileşimli Olarak Saat Denetimi
A <xref:System.Windows.Media.Animation.Clock> nesnenin <xref:System.Windows.Media.Animation.ClockController> özelliği etkileşimli olarak başlatın, duraklatma, sürdürme, arama, dolgu süresinin ilerletme ve saati olanak sağlar. Yalnızca kök saatin zamanlama ağacının etkileşimli olarak denetlenebilir.  
  
> [!NOTE]
>  Etkileşimli olarak doğrudan saatlerle çalışmanızı gerektirmeyen denetim animasyonlar farklı yöntemleri vardır: film şeridi de kullanabilirsiniz. Görsel Taslaklar işaretleme ve kod desteklenir. Bir örnek için bkz. [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md) veya [animasyona genel bakış](animation-overview.md).  
  
 Aşağıdaki örnekte, çeşitli düğmeler, etkileşimli bir animasyon saat denetimi için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animasyona Genel bakış](animation-overview.md)
