---
title: 'Nasıl yapılır: Zaman Çizelgesinin Hızını Değiştirmeden Saat Hızını Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 126d260fbd59c1c35d8f56be6aa7dabe7688fa32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a>Nasıl yapılır: Zaman Çizelgesinin Hızını Değiştirmeden Saat Hızını Değiştirme
A <xref:System.Windows.Media.Animation.ClockController> nesnenin <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> özelliği sağlar, hızını değiştirmek bir <xref:System.Windows.Media.Animation.Clock> değiştirmeden <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> saatin <xref:System.Windows.Media.Animation.Timeline>. Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.ClockController> etkileşimli olarak değiştirmek için kullanılan <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> bir saat. <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> Olay ve saatin <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> saatin geçerli genel hızını görüntülemek için kullanılan özellik her zaman kendi etkileşimli <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> değiştirilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
