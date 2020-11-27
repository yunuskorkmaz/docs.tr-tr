---
title: WF 'de durum makinesi etkinlikleri
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: dd0bfae1f24ecd9f98c0a2f04265581f880202a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261728"
---
# <a name="state-machine-activities-in-wf"></a>WF 'de durum makinesi etkinlikleri

.NET Framework 4,5, durum makine iş akışları oluşturmak için sistem tarafından sağlanan çeşitli etkinlikler ve etkinlik tasarımcıları sağlar.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Bilinen durum makinesi paradigmasını kullanarak içerilen etkinlikleri yürütür.|  
|<xref:System.Activities.Statements.State>|Durum makinesindeki bir durumu temsil eder.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Bir durum makinesindeki sonlandırma durumunu temsil eder. <xref:System.Activities.Core.Presentation.FinalState> , kullanıldığında <xref:System.Activities.Statements.State> sonlandırma durumu olarak önceden yapılandırılmış bir oluşturma işlemi oluşturduğunda etkinlik tasarlayıcıdır. Daha fazla bilgi için bkz. [FinalState etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|İki durum arasındaki geçişi temsil eder. İçin **araç kutusu** öğesi yok <xref:System.Activities.Statements.Transition> ; iki durum arasında bir satırı sürükleyip bırakarak veya bir durum diğerinin üzerine geldiğinde görüntülenen üçgenlerde bir durum bırakarak iş akışı tasarımcısında geçişler oluşturulur. Daha fazla bilgi için bkz. [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Öğreticisi](getting-started-tutorial.md)
