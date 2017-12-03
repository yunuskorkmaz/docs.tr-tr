---
title: "Yordam iş akışları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd879d138a95c003ca0ffb12b3ce010534c3e158
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="procedural-workflows"></a>Yordam iş akışları
Yordam iş akışları yordam dillerinde bulunan benzer akış denetimi yöntemlerini kullanın. Bu yapıları içermek `While` ve `If`. Bu iş akışları gibi diğer akış denetimi etkinlikleri kullanarak serbestçe birleştirilebilen <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Yürütme akışı denetimi  
 İş akışı etkinlik kütüphanesini yordam dillerde kullanılan çoğu akış denetimi yöntemleri modelleme için etkinlikler içeriyor. Bu güncelleştirmeler şunlardır:  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Akış denetimi etkinlikleri kullanmak için sürükleyip onlardan **etkinlik** bileşik etkinliği Tasarımcı penceresinin içinde içine araç.  
  
> [!NOTE]
>  Kullanıyorsanız [!INCLUDE[dublin](../../../includes/dublin-md.md)] ana iş akışları bir Web grubunda AppFabric örnekleri farklı AppFabric sunucular arasında taşınır. Bu kaynaklar tüm düğümler arasında paylaşılan mümkün olmasını gerektirir.  Varsayılan NET 4 iş akışı etkinlikleri hiçbiri yerel kaynaklara erişmek herhangi bir işlem içerir. Bir geliştirici AppFabric iş akışı immovable olarak işaretlemek için herhangi bir mekanizma sunmaz olduğundan, bir iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Akış Çizelgesi iş akışları](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
