---
title: WF etkinlikleri temelleri
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: d87125d8d85fa33a49651dfabb840881b0e216ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513382"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="975f2-102">WF etkinlikleri temelleri</span><span class="sxs-lookup"><span data-stu-id="975f2-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="975f2-103"> yaygın görevleri gerçekleştirmek için uygun bir mekanizmaya birkaç sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="975f2-103"> provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="975f2-104">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="975f2-104">Activity</span></span>|<span data-ttu-id="975f2-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="975f2-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="975f2-106">Geçerli kapsamda bir değişkene değer atayan.</span><span class="sxs-lookup"><span data-stu-id="975f2-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="975f2-107">Bir yol yürütme büyük olasılıkla boşaltılması için iş akışı izin vererek bir boşta durumuna geçirir.</span><span class="sxs-lookup"><span data-stu-id="975f2-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="975f2-108">Türetilen bir temsilcisini yürütür <xref:System.Activities.ActivityDelegate> ve bir özellik olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="975f2-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="975f2-109">CLR nesnesine ortak bir yöntem yürütür.</span><span class="sxs-lookup"><span data-stu-id="975f2-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="975f2-110">Belirtilen dizenin konsol veya belirtilen Yazar <xref:System.IO.TextWriter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="975f2-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
