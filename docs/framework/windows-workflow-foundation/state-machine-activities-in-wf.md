---
description: "Hakkında daha fazla bilgi edinin: WF 'de durum makinesi etkinlikleri"
title: WF 'de durum makinesi etkinlikleri
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 4571bdbabc30e721523ae18449454627c0bf7319
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755258"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="fb2d5-103">WF 'de durum makinesi etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="fb2d5-103">State Machine Activities in WF</span></span>

<span data-ttu-id="fb2d5-104">.NET Framework 4,5, durum makine iş akışları oluşturmak için sistem tarafından sağlanan çeşitli etkinlikler ve etkinlik tasarımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-104">.NET Framework 4.5 provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="fb2d5-105">Bilinen durum makinesi paradigmasını kullanarak içerilen etkinlikleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-105">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="fb2d5-106">Durum makinesindeki bir durumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-106">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="fb2d5-107">Bir durum makinesindeki sonlandırma durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-107">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="fb2d5-108"><xref:System.Activities.Core.Presentation.FinalState> , kullanıldığında <xref:System.Activities.Statements.State> sonlandırma durumu olarak önceden yapılandırılmış bir oluşturma işlemi oluşturduğunda etkinlik tasarlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-108"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="fb2d5-109">Daha fazla bilgi için bkz. [FinalState etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="fb2d5-109">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="fb2d5-110">İki durum arasındaki geçişi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-110">Represents the transition between two states.</span></span> <span data-ttu-id="fb2d5-111">İçin **araç kutusu** öğesi yok <xref:System.Activities.Statements.Transition> ; iki durum arasında bir satırı sürükleyip bırakarak veya bir durum diğerinin üzerine geldiğinde görüntülenen üçgenlerde bir durum bırakarak iş akışı tasarımcısında geçişler oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-111">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="fb2d5-112">Daha fazla bilgi için bkz. [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="fb2d5-112">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb2d5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb2d5-113">See also</span></span>

- [<span data-ttu-id="fb2d5-114">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="fb2d5-114">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
