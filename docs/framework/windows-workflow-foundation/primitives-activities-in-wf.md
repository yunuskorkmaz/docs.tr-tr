---
title: WF 'de temel elemanlar etkinlikleri
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: 4f2c20c109d67a35ccc9c363c0a3631922161d2c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246083"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="cace7-102">WF 'de temel elemanlar etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="cace7-102">Primitives Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="cace7-103">ortak görevleri gerçekleştirmek için kullanışlı bir mekanizma sağlayan, sistem tarafından sağlanan çeşitli etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cace7-103">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="cace7-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="cace7-104">Activity</span></span>|<span data-ttu-id="cace7-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cace7-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="cace7-106">Geçerli kapsamdaki bir değişkene bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="cace7-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="cace7-107">Yürütmenin bir yolunu boşta durumuna geçirir, muhtemelen iş akışının kaldırılabilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="cace7-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="cace7-108"><xref:System.Activities.ActivityDelegate>, Bir özellik olarak sunulur ve öğesinden türetilen bir temsilciyi yürütür.</span><span class="sxs-lookup"><span data-stu-id="cace7-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="cace7-109">CLR nesnesinin ortak bir yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="cace7-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="cace7-110">Belirtilen bir dizeyi konsola veya belirtilen <xref:System.IO.TextWriter> nesneye yazar.</span><span class="sxs-lookup"><span data-stu-id="cace7-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
