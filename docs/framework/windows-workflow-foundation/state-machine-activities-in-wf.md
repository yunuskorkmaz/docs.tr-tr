---
title: WF Durum makinesi etkinlikleri
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 3086348d1c4f29e3f446e9525a12a9c207efb328
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619006"
---
# <a name="state-machine-activities-in-wf"></a>WF Durum makinesi etkinlikleri
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] çeşitli sistem tarafından sağlanan etkinlikleri ve etkinlik tasarımcıları, durum makine iş akışları oluşturmak için sağlar.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Tanıdık durum makine paradigması kullanarak içerilen etkinlikleri yürütür.|  
|<xref:System.Activities.Statements.State>|Bir durum makinesindeki bir durumu temsil eder.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Bir durum makinesindeki Sonlandırıcı bir durumu temsil eder. <xref:System.Activities.Core.Presentation.FinalState> bir etkinlik Tasarımcısı olduğunda kullanılan oluşturur bir <xref:System.Activities.Statements.State> Sonlandırıcı bir durum önceden yapılandırılmış. Daha fazla bilgi için [FinalState etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|İki durum arasında geçiş temsil eder. Yok hiçbir **araç kutusu** için madde <xref:System.Activities.Statements.Transition>; geçişleri iki durum arasında bir satır sürükleyip bırakarak iş akışı Tasarımcısı üzerinde oluşturulur veya görünür üçgenler durumuna bırakarak bir durumdan başka bir vurgulanan . Daha fazla bilgi için [Transition etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
