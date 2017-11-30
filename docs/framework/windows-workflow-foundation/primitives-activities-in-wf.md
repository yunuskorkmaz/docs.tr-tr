---
title: WF etkinlikleri temelleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0bd34984b421f353c53da8c97533b396a49751d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="8e08c-102">WF etkinlikleri temelleri</span><span class="sxs-lookup"><span data-stu-id="8e08c-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="8e08c-103">yaygın görevleri gerçekleştirmek için uygun bir mekanizmaya birkaç sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e08c-103"> provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="8e08c-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="8e08c-104">Activity</span></span>|<span data-ttu-id="8e08c-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e08c-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="8e08c-106">Geçerli kapsamda bir değişkene değer atayan.</span><span class="sxs-lookup"><span data-stu-id="8e08c-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="8e08c-107">Bir yol yürütme büyük olasılıkla boşaltılması için iş akışı izin vererek bir boşta durumuna geçirir.</span><span class="sxs-lookup"><span data-stu-id="8e08c-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="8e08c-108">Türetilen bir temsilcisini yürütür <xref:System.Activities.ActivityDelegate> ve bir özellik olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8e08c-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="8e08c-109">CLR nesnesine ortak bir yöntem yürütür.</span><span class="sxs-lookup"><span data-stu-id="8e08c-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="8e08c-110">Belirtilen dizenin konsol veya belirtilen Yazar <xref:System.IO.TextWriter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8e08c-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
