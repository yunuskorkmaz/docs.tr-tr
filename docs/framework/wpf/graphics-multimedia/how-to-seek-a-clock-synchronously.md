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
ms.openlocfilehash: 9b6b1f5523effc56ccd9ddaa4f478e1d3a20ada8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651265"
---
# <a name="how-to-seek-a-clock-synchronously"></a>Nasıl yapılır: Saati Zaman Uyumlu Olarak Arama
Kullanım <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> belirli bir noktaya saati zaman uyumlu olarak arama için yöntemi. Aşağıdaki örnek, her ikisi de gösterir <xref:System.Windows.Media.Animation.ClockController.Seek%2A> ve <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> yöntemlerinin bir <xref:System.Windows.Media.Animation.ClockController>.  
  
 Bu örnek nasıl aranacağını gösterir bir <xref:System.Windows.Media.Animation.Clock>; bir görsel taslak arama nasıl gösteren bir örnek için [bir görsel taslağı zaman uyumlu olarak arama](how-to-seek-a-storyboard-synchronously.md) .  
  
## <a name="example"></a>Örnek  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](~/samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
