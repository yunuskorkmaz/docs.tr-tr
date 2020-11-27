---
title: Etkinlik sınıfını kullanarak iş akışı etkinliği yazma
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 21f1c8b1249d41029fa7a19360e96ad866c823a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293851"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="e0883-102">Etkinlik sınıfını kullanarak iş akışı etkinliği yazma</span><span class="sxs-lookup"><span data-stu-id="e0883-102">Workflow Activity Authoring Using the Activity Class</span></span>

<span data-ttu-id="e0883-103">' De Windows Workflow Foundation (WF) kullanarak bir etkinlik oluşturmanın en temel yolu, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <xref:System.Activities.Activity> [yerleşik etkinlik kitaplığından](net-framework-4-5-built-in-activity-library.md)özel etkinlikleri veya etkinlikleri derleyerek Bu işlevden devralan bir sınıf oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e0883-103">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="e0883-104">Bu konuda, konsola iki ileti yazan bir etkinliğin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0883-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="e0883-105">Etkinlik tasarımcısını kullanarak özel bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0883-105">To create a custom Activity using the activity designer</span></span>

1. <span data-ttu-id="e0883-106">Visual Studio 2012 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="e0883-106">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="e0883-107">Dosya, yeni, proje ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e0883-107">Select File, New, Project.</span></span> <span data-ttu-id="e0883-108">**Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="e0883-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="e0883-109">**Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e0883-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="e0883-110">Yeni proje Merhaba etkinliğini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e0883-110">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="e0883-111">Yeni etkinliği açın.</span><span class="sxs-lookup"><span data-stu-id="e0883-111">Open the new activity.</span></span>  <span data-ttu-id="e0883-112"><xref:System.Activities.Statements.Sequence>Araç kutusundan bir etkinliği tasarımcı yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e0883-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4. <span data-ttu-id="e0883-113">Etkinliği etkinliğe sürükleyin <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="e0883-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="e0883-114">`"Hello World"` **Metin** alanına (tırnak işareti ile) girin.</span><span class="sxs-lookup"><span data-stu-id="e0883-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5. <span data-ttu-id="e0883-115">İkinci bir <xref:System.Activities.Statements.WriteLine> etkinliği <xref:System.Activities.Statements.Sequence> , birincinin altında, etkinliğe sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e0883-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="e0883-116">`"Goodbye"` **Metin** alanına (tırnak işareti ile) girin.</span><span class="sxs-lookup"><span data-stu-id="e0883-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
