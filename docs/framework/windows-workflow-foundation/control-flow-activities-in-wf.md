---
title: WF 'de denetim akışı etkinlikleri
description: Bu makalede, bir iş akışı içinde yürütme akışını denetlemek için .NET Framework 4.6.1 etkinlikleri özetlenmektedir.
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: 18ff982d3f215e3fd46108eb2411f3d1a5ab9745
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420077"
---
# <a name="control-flow-activities-in-wf"></a>WF 'de denetim akışı etkinlikleri
, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Bir iş akışı içinde yürütme akışını denetlemek için çeşitli etkinlikler sağlar. Bu etkinliklerin bazıları ( `Switch` ve gibi `If` ), Visual C# gibi programlama ortamlarından benzer şekilde akış denetim yapılarını uygular, diğerleri ise `Pick` yeni programlama yapılarını modelleyebilir.  
  
 `Parallel`Ve etkinlikleri gibi etkinliklerin `ParallelForEach` birden çok alt etkinliği aynı anda yürütmeye zamanlarken, iş akışı için yalnızca tek bir iş parçacığının kullanıldığını unutmayın. Bu etkinliklerin her bir alt etkinliği sırayla yürütülür ve önceki etkinlikler tamamlanana veya boşta olana kadar ardışık etkinlikler yürütülmez. Sonuç olarak, bu etkinlikler birçok olası engelleme etkinliklerinin araya eklemeli bir biçimde yürütülmesi gereken uygulamalar için en yararlı seçenektir. Bu etkinliklerin alt etkinliklerinin hiçbiri boşta kalırsa, etkinlik tıpkı etkinlik gibi `Parallel` yürütülür ve etkinlik tıpkı `Sequence` `ParallelForEach` etkinlik gibi yürütülür `ForEach` . Ancak, zaman uyumsuz etkinlikler (örneğin, öğesinden türetilen etkinlikler <xref:System.Activities.AsyncCodeActivity> ) veya mesajlaşma etkinlikleriyle birlikte kullanılırsa, alt etkinlik iletinin alınmasını veya zaman uyumsuz işinin tamamlanmasını beklediği sırada denetim sonraki dala geçer.  
  
## <a name="flow-control-activities"></a>Akış denetim etkinlikleri  
  
|Etkinlik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|İçerilen etkinlikleri bir kez yürütür ve bir koşul olduğunda bunu yapmaya devam eder `true` .|  
|<xref:System.Activities.Statements.ForEach%601>|Bir koleksiyondaki her öğe için sırayla gömülü bir ifade yürütür. <xref:System.Activities.Statements.ForEach%601>, anahtar sözcüğüne benzerdir `foreach` , ancak bir dil ifadesinin yerine etkinlik olarak uygulanır.|  
|<xref:System.Activities.Statements.If>|Bir koşul varsa içerilen etkinlikleri yürütür `true` ve <xref:System.Activities.Statements.If.Else%2A> Koşul ise özellikte içerilen etkinlikleri yürütebilir `false` .|  
|<xref:System.Activities.Statements.Parallel>|İçerilen etkinlikleri paralel olarak yürütür.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Bir koleksiyondaki her öğe için gömülü bir ifadeyi paralel olarak yürütür.|  
|<xref:System.Activities.Statements.Pick>|Olay tabanlı denetim akışı modelleme sağlar.|  
|<xref:System.Activities.Statements.PickBranch>|Bir etkinlikte yürütmenin olası yolunu temsil eder <xref:System.Activities.Statements.Pick> .|  
|<xref:System.Activities.Statements.Sequence>|İçerilen etkinlikleri sırayla yürütür.|  
|<xref:System.Activities.Statements.Switch%601>|Belirli bir ifadenin değerine bağlı olarak, çalıştırılacak sayıda etkinlikten bir seçim seçer.|  
|<xref:System.Activities.Statements.While>|Bir koşul olduğunda içerilen etkinlikleri yürütür `true` .|
