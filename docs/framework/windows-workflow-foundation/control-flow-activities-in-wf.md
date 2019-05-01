---
title: WF akış etkinliği
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: bcbb12210af2d0172977dca6f81355031baa043a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945918"
---
# <a name="control-flow-activities-in-wf"></a>WF akış etkinliği
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Çeşitli etkinlikler, bir iş akışındaki yürütmenin akışını denetlemek için sağlar. Bu etkinliklerin bazıları (gibi `Switch` ve `If`) akış denetim yapıları ortamları Visual gibi programlama benzer uygulamak C#, başkalarının çalışırken (gibi `Pick`) yeni programlama yapıları model.  
  
 Etkinlikleri sırasında gibi unutmayın `Parallel` ve `ParallelForEach` etkinlikleri birden çok alt etkinlik yürütmesi için aynı anda zamanlayın, tek bir iş parçacığı bir iş akışı için kullanılır. Her bir alt etkinlik bu etkinlikleri sırayla yürütür ve ardışık etkinlikler önceki etkinliklere tamamlamak veya boşta Git kadar yürütülmez. Sonuç olarak, bu etkinlikler birkaç olası engelleme etkinliği bir araya eklemeli biçimde yürütülmesi gereken uygulamalar için en kullanışlıdır. Bu etkinliklerin alt etkinliklerin hiçbiri boş giderseniz bir `Parallel` etkinliği yürütür olduğu gibi bir `Sequence` etkinliği ve bir `ParallelForEach` etkinliği yürütür olduğu gibi bir `ForEach` etkinlik. Eğer, ancak zaman uyumsuz etkinlikler (türetilen etkinlikleri gibi <xref:System.Activities.AsyncCodeActivity>) veya Mesajlaşma etkinlikleri kullanılır, denetimi kendi ileti alınabilmesi bir alt etkinlik beklediği sırada sonraki dal ya da tamamlanacak zaman uyumsuz çalışmasını geçecek.  
  
## <a name="flow-control-activities"></a>Akış denetimi etkinlikleri  
  
|Etkinlik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|İçerilen etkinlikleri bir kez çalıştırır ve bir koşulu sırada bunu yapmak devam `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Sıralı bir koleksiyondaki her öğe için bir katıştırılmış deyim yürütür. <xref:System.Activities.Statements.ForEach%601> anahtar sözcük benzer `foreach`, ancak bir dil ifadesi yerine bir etkinlik olarak uygulanır.|  
|<xref:System.Activities.Statements.If>|Bir koşul ise, içerilen etkinlikleri yürütür `true`ve içerdiği etkinlikler yürütebilir <xref:System.Activities.Statements.If.Else%2A> koşul ise özellik `false`.|  
|<xref:System.Activities.Statements.Parallel>|İçerilen etkinlikleri paralel olarak yürütür.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Bir koleksiyondaki her öğe için paralel bir katıştırılmış deyim yürütür.|  
|<xref:System.Activities.Statements.Pick>|Olay tabanlı denetim akış modelleme sağlar.|  
|<xref:System.Activities.Statements.PickBranch>|Olası bir yürütme yolunu temsil ettiği bir <xref:System.Activities.Statements.Pick> etkinlik.|  
|<xref:System.Activities.Statements.Sequence>|İçerilen etkinlikleri sırayla yürütür.|  
|<xref:System.Activities.Statements.Switch%601>|Bir seçenek, belirli bir ifadenin değerine göre yürütmek için etkinlikler arasında bir sayı seçer.|  
|<xref:System.Activities.Statements.While>|İçerilen etkinlikleri bir koşulu sırada yürütür `true`.|
