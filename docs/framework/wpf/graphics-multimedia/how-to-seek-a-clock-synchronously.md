---
title: "Nasıl yapılır: Saati Zaman Uyumlu Olarak Arama"
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
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d158629b428bda8e7749df393ad0724225b5a0a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-seek-a-clock-synchronously"></a>Nasıl yapılır: Saati Zaman Uyumlu Olarak Arama
Kullanım <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> belirli bir noktaya saati zaman uyumlu arama yöntemi. Aşağıdaki örnek, her ikisi de gösterir <xref:System.Windows.Media.Animation.ClockController.Seek%2A> ve <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> yöntemlerinin bir <xref:System.Windows.Media.Animation.ClockController>.  
  
 Bu örnek nasıl aranacağını gösterir bir <xref:System.Windows.Media.Animation.Clock>; film şeridi arama nasıl gösteren bir örnek için [eşzamanlı film şeridi arama](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md) .  
  
## <a name="example"></a>Örnek  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
