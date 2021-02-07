---
description: 'Daha fazla bilgi edinin: etkinlik sınıfını kullanarak Iş akışı etkinliği yazma'
title: Etkinlik sınıfını kullanarak iş akışı etkinliği yazma
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 0d3ffc88bacfd941dfa0c853991bf72045468323
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754946"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="12fd2-103">Etkinlik sınıfını kullanarak iş akışı etkinliği yazma</span><span class="sxs-lookup"><span data-stu-id="12fd2-103">Workflow Activity Authoring Using the Activity Class</span></span>

<span data-ttu-id="12fd2-104">' De Windows Workflow Foundation (WF) kullanarak bir etkinlik oluşturmanın en temel yolu, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <xref:System.Activities.Activity> [yerleşik etkinlik kitaplığından](net-framework-4-5-built-in-activity-library.md)özel etkinlikleri veya etkinlikleri derleyerek Bu işlevden devralan bir sınıf oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="12fd2-104">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="12fd2-105">Bu konuda, konsola iki ileti yazan bir etkinliğin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="12fd2-105">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="12fd2-106">Etkinlik tasarımcısını kullanarak özel bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="12fd2-106">To create a custom Activity using the activity designer</span></span>

1. <span data-ttu-id="12fd2-107">Visual Studio 2012 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="12fd2-107">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="12fd2-108">Dosya, yeni, proje ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="12fd2-108">Select File, New, Project.</span></span> <span data-ttu-id="12fd2-109">**Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="12fd2-109">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="12fd2-110">**Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="12fd2-110">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="12fd2-111">Yeni proje Merhaba etkinliğini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="12fd2-111">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="12fd2-112">Yeni etkinliği açın.</span><span class="sxs-lookup"><span data-stu-id="12fd2-112">Open the new activity.</span></span>  <span data-ttu-id="12fd2-113"><xref:System.Activities.Statements.Sequence>Araç kutusundan bir etkinliği tasarımcı yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="12fd2-113">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4. <span data-ttu-id="12fd2-114">Etkinliği etkinliğe sürükleyin <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="12fd2-114">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="12fd2-115">`"Hello World"` **Metin** alanına (tırnak işareti ile) girin.</span><span class="sxs-lookup"><span data-stu-id="12fd2-115">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5. <span data-ttu-id="12fd2-116">İkinci bir <xref:System.Activities.Statements.WriteLine> etkinliği <xref:System.Activities.Statements.Sequence> , birincinin altında, etkinliğe sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="12fd2-116">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="12fd2-117">`"Goodbye"` **Metin** alanına (tırnak işareti ile) girin.</span><span class="sxs-lookup"><span data-stu-id="12fd2-117">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
