---
title: WF etkinliklerini temelleri
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: d87125d8d85fa33a49651dfabb840881b0e216ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780711"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="40bd3-102">WF etkinliklerini temelleri</span><span class="sxs-lookup"><span data-stu-id="40bd3-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="40bd3-103">Ortak görevleri gerçekleştirmek için kullanışlı bir mekanizma sağlayan birkaç sistem tarafından sağlanan etkinliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="40bd3-103">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="40bd3-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="40bd3-104">Activity</span></span>|<span data-ttu-id="40bd3-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40bd3-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="40bd3-106">Geçerli kapsamda bir değişkene bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="40bd3-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="40bd3-107">Bir yürütme yolu büyük olasılıkla kaldırılacak iş akışını sağlayan boş bir duruma koyar.</span><span class="sxs-lookup"><span data-stu-id="40bd3-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="40bd3-108">Türetilen bir temsilcisini yürütür <xref:System.Activities.ActivityDelegate> ve bir özellik olarak kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="40bd3-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="40bd3-109">CLR nesnesi genel bir yöntem yürütür.</span><span class="sxs-lookup"><span data-stu-id="40bd3-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="40bd3-110">Belirtilen bir dizenin konsol veya belirtilen bir yazar <xref:System.IO.TextWriter> nesne.</span><span class="sxs-lookup"><span data-stu-id="40bd3-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
