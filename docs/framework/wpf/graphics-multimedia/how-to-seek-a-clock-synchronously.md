---
title: 'Nasıl yapılır: Saati Zaman Uyumlu Olarak Arama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
ms.openlocfilehash: d8e7b0f4bfa3a59814d87bfb6d7e8b40bd80f6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559863"
---
# <a name="how-to-seek-a-clock-synchronously"></a>Nasıl yapılır: Saati Zaman Uyumlu Olarak Arama
Kullanım <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> belirli bir noktaya saati zaman uyumlu arama yöntemi. Aşağıdaki örnek, her ikisi de gösterir <xref:System.Windows.Media.Animation.ClockController.Seek%2A> ve <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> yöntemlerinin bir <xref:System.Windows.Media.Animation.ClockController>.  
  
 Bu örnek nasıl aranacağını gösterir bir <xref:System.Windows.Media.Animation.Clock>; film şeridi arama nasıl gösteren bir örnek için [eşzamanlı film şeridi arama](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md) .  
  
## <a name="example"></a>Örnek  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
