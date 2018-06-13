---
title: WF etkinlikleri Durum makinesi
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 78727bab0102909e9f1e479210cf4b42801aa3ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515775"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="e3a45-102">WF etkinlikleri Durum makinesi</span><span class="sxs-lookup"><span data-stu-id="e3a45-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="e3a45-103"> birkaç sistem tarafından sağlanan etkinlikleri ve etkinlik tasarımcıları durumu makine iş akışları oluşturmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3a45-103"> provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="e3a45-104">Tanıdık durumu makine kip kullanarak içerilen etkinlikleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="e3a45-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="e3a45-105">Durum makinesinin durumda temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3a45-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="e3a45-106">Durum makinesinin sonlandırma durumunda temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3a45-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="e3a45-107"><xref:System.Activities.Core.Presentation.FinalState> bir etkinlik Tasarımcısı olduğunda kullanılan oluşturur bir <xref:System.Activities.Statements.State> sonlandırma durumu olarak yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="e3a45-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="e3a45-108">Daha fazla bilgi için bkz: [son durum etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="e3a45-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="e3a45-109">İki durumlu arasında geçiş temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3a45-109">Represents the transition between two states.</span></span> <span data-ttu-id="e3a45-110">Yoktur hiçbir **araç** için madde <xref:System.Activities.Statements.Transition>; geçişleri arasında iki durumlu bir satır bırakarak iş akışı Tasarımcısı oluşturulur veya ne zaman görünür üçgenler bir durumda bırakarak durum başka bir üzerine getirildiği .</span><span class="sxs-lookup"><span data-stu-id="e3a45-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="e3a45-111">Daha fazla bilgi için bkz: [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="e3a45-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3a45-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3a45-112">See Also</span></span>  
 [<span data-ttu-id="e3a45-113">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="e3a45-113">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
