---
title: "WF akış etkinliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5312012a74f5e11b02c0191dc00fa23fb25a73a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="control-flow-activities-in-wf"></a>WF akış etkinliği
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Bir iş akışındaki akışını denetlemek için çeşitli etkinlikler sağlar. Bu etkinliklerin bazıları (gibi `Switch` ve `If`) akış denetim yapıları benzer ortamları gibi programlama uygulamak [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], diğerleri while (gibi `Pick`) modeli yeni programlama yapıları.  
  
 Etkinlikleri sırasında gibi unutmayın `Parallel` ve `ParallelForEach` etkinlikleri zamanlama yürütme için birden çok alt etkinlikler aynı anda, yalnızca tek bir iş parçacığı için iş akışı kullanılır. Bu etkinliklerin her alt etkinlik sıralı olarak yürütür ve önceki etkinliklerini tamamlamak veya boşta Git kadar ardışık etkinlikleri yürütülmez. Sonuç olarak, bu etkinlikler birkaç olası engelleme etkinlikleri bir araya eklemeli şekilde yürütülmelidir uygulamalar için en kullanışlıdır. Bu etkinlikler alt etkinliklerini hiçbiri boşta kalırsa bir `Parallel` etkinlik yürütür tıpkı bir `Sequence` etkinliği ve bir `ParallelForEach` etkinlik yürütür tıpkı bir `ForEach` etkinlik. Eğer, ancak, zaman uyumsuz etkinlikleri (öğesinden türetilen etkinlikleri gibi <xref:System.Activities.AsyncCodeActivity>) veya Mesajlaşma etkinlikleri kullanılır, Denetim alt etkinlik alınabilmesi kendi ileti beklerken sonraki şube veya tamamlanması için zaman uyumsuz çalışmasını geçecek.  
  
## <a name="flow-control-activities"></a>Akış denetimi etkinlikleri  
  
|Etkinlik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|İçerilen etkinlikleri bir kez çalıştırır ve bir koşul olsa da bunu yapmak devam `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Bir koleksiyondaki her öğe için sıralı bir katıştırılmış deyimini yürütür. <xref:System.Activities.Statements.ForEach%601>anahtar sözcüğüne benzer `foreach`, bir dil deyimi yerine bir etkinlik olarak uygulanan ancak.|  
|<xref:System.Activities.Statements.If>|Bir koşul ise, içerilen etkinlikleri yürütür `true`ve içerdiği etkinlikleri yürütebilir <xref:System.Activities.Statements.If.Else%2A> koşul ise özelliği `false`.|  
|<xref:System.Activities.Statements.Parallel>|İçerilen etkinlikleri paralel olarak yürütür.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Bir koleksiyondaki her öğe için paralel bir katıştırılmış deyimini yürütür.|  
|<xref:System.Activities.Statements.Pick>|Olay tabanlı denetim akışı modelleme sağlar.|  
|<xref:System.Activities.Statements.PickBranch>|Yürütme olası bir yolu temsil eden bir <xref:System.Activities.Statements.Pick> etkinlik.|  
|<xref:System.Activities.Statements.Sequence>|İçerilen etkinlikleri sırayla yürütür.|  
|<xref:System.Activities.Statements.Switch%601>|Bir seçenek değerine göre belirli bir deyim yürütmek için etkinlikler arasında bir sayı seçer.|  
|<xref:System.Activities.Statements.While>|Bir koşul ederken içerilen etkinlikleri yürütür `true`.|
