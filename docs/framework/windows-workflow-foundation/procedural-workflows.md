---
title: Yordam iş akışları
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 29fc6f5ebd6bf1984f287c3d407d2564249c65f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500544"
---
# <a name="procedural-workflows"></a>Yordam iş akışları
Yordam iş akışları, akış denetimi yöntemleri yordam dillerinde bulunan benzer kullanın. Bu yapılar dahil `While` ve `If`. Bu iş akışları gibi diğer akış denetimi etkinlikleri kullanarak serbestçe oluşturulabildikleri <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Yürütme akışı denetimi  
 İş akışı etkinlik kitaplığı yordam dilde kullanılan çoğu akış denetimi yöntemleri modelleme için etkinlikleri içerir. Bu güncelleştirmeler şunlardır:  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Akış denetimi etkinlikleri kullanmak için sürükleyip bunları **etkinlik** Tasarımcı penceresinin içinde bileşik bir etkinlik araç.  
  
> [!NOTE]
>  Kullanıyorsanız [!INCLUDE[dublin](../../../includes/dublin-md.md)] bir Web grubundaki konak iş akışlarına AppFabric örnekleri farklı AppFabric sunucular arasında taşınır. Bu, kaynakları tüm düğümler arasında paylaşılacak mümkün olmasını gerektirir.  Varsayılan ağ 4 iş akışı etkinlikleri hiçbiri yerel kaynaklara erişen herhangi bir işlem içerir. İş akışı immovable olarak işaretlemek için herhangi bir mekanizma AppFabric sunmaz olduğundan, bir geliştirici iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Akış Çizelgesi İş Akışları](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
