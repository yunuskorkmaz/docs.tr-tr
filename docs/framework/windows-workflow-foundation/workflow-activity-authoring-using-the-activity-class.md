---
title: "Etkinlik sınıfını kullanarak etkinliği iş akışı yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52d29f9cbed65932b3f9e97f0e9275861953b5d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="2c273-102">Etkinlik sınıfını kullanarak etkinliği iş akışı yazma</span><span class="sxs-lookup"><span data-stu-id="2c273-102">Workflow Activity Authoring Using the Activity Class</span></span>
<span data-ttu-id="2c273-103">Kullanarak bir etkinlik oluşturmak için en temel yolu [!INCLUDE[wf](../../../includes/wf-md.md)] içinde [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] öğesinden devralınan bir sınıf oluşturmak için <xref:System.Activities.Activity> işlevselliği birleştirerek özel oluşturan etkinlikler veya etkinliklerden [yerleşik etkinlik kitaplığı ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="2c273-103">The most basic way to create an activity using [!INCLUDE[wf](../../../includes/wf-md.md)] in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="2c273-104">Bu konuda iki ileti konsola bir etkinlik oluşturma gösterilir.</span><span class="sxs-lookup"><span data-stu-id="2c273-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="2c273-105">Etkinlik Tasarımcısı'nı kullanarak bir özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2c273-105">To create a custom Activity using the activity designer</span></span>  
  
1.  <span data-ttu-id="2c273-106">Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c273-106">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c273-107">Dosya, yeni, proje'i seçin.</span><span class="sxs-lookup"><span data-stu-id="2c273-107">Select File, New, Project.</span></span> <span data-ttu-id="2c273-108">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="2c273-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2c273-109">Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="2c273-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="2c273-110">Yeni Proje HelloActivity olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="2c273-110">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="2c273-111">Yeni Etkinlik açın.</span><span class="sxs-lookup"><span data-stu-id="2c273-111">Open the new activity.</span></span>  <span data-ttu-id="2c273-112">Sürükleme bir <xref:System.Activities.Statements.Sequence> Tasarımcı yüzeyine araç etkinliğinden.</span><span class="sxs-lookup"><span data-stu-id="2c273-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>  
  
4.  <span data-ttu-id="2c273-113">Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2c273-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="2c273-114">Girin `"Hello World"` (ile tırnak işaretleri) içine **metin** alan.</span><span class="sxs-lookup"><span data-stu-id="2c273-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>  
  
5.  <span data-ttu-id="2c273-115">İkinci bir sürükleyin <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> ilk aşağıda etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2c273-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="2c273-116">Girin `"Goodbye"` (ile tırnak işaretleri) içine **metin** alan.</span><span class="sxs-lookup"><span data-stu-id="2c273-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
