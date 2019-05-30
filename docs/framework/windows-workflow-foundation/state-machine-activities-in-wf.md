---
title: WF Durum makinesi etkinlikleri
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 64af2698c878066464e2ca3f32d4522d99999aec
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378046"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="c3c9b-102">WF Durum makinesi etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="c3c9b-102">State Machine Activities in WF</span></span>
<span data-ttu-id="c3c9b-103">.NET framework 4.5, durum makine iş akışları oluşturmak için çeşitli sistem tarafından sağlanan etkinlikleri ve etkinlik tasarımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3c9b-103">.NET Framework 4.5 provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="c3c9b-104">Tanıdık durum makine paradigması kullanarak içerilen etkinlikleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="c3c9b-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="c3c9b-105">Bir durum makinesindeki bir durumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3c9b-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="c3c9b-106">Bir durum makinesindeki Sonlandırıcı bir durumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3c9b-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="c3c9b-107"><xref:System.Activities.Core.Presentation.FinalState> bir etkinlik Tasarımcısı olduğunda kullanılan oluşturur bir <xref:System.Activities.Statements.State> Sonlandırıcı bir durum önceden yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="c3c9b-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="c3c9b-108">Daha fazla bilgi için [FinalState etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="c3c9b-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="c3c9b-109">İki durum arasında geçiş temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3c9b-109">Represents the transition between two states.</span></span> <span data-ttu-id="c3c9b-110">Yok hiçbir **araç kutusu** için madde <xref:System.Activities.Statements.Transition>; geçişleri iki durum arasında bir satır sürükleyip bırakarak iş akışı Tasarımcısı üzerinde oluşturulur veya görünür üçgenler durumuna bırakarak bir durumdan başka bir vurgulanan .</span><span class="sxs-lookup"><span data-stu-id="c3c9b-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="c3c9b-111">Daha fazla bilgi için [Transition etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="c3c9b-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3c9b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3c9b-112">See also</span></span>

- [<span data-ttu-id="c3c9b-113">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="c3c9b-113">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
