---
title: "Başka bir olay günlüğü bu ada sahip bir kaynak zaten kaydettirildi"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="22dff-102">Başka bir olay günlüğü bu ada sahip bir kaynak zaten kaydettirildi</span><span class="sxs-lookup"><span data-stu-id="22dff-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="22dff-103">Bir olay günlüğüne bir giriş yazmak için belirtilen kaynak ile başka bir olay günlüğü, kayıtlı çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="22dff-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="22dff-104">Ayarlamalısınız <xref:System.Diagnostics.EventLog.Source%2A> özelliği, <xref:System.Diagnostics.EventLog> bileşeniniz bir giriş bir günlük dosyasına yazar önce bileşen örneği.</span><span class="sxs-lookup"><span data-stu-id="22dff-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="22dff-105">Bu durumda, sistem, belirtilen kaynak bileşeni yazma olay günlüğü ve çağrıları ile kaydedildiğini denetler <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="22dff-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="22dff-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="22dff-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="22dff-107">İlk günlük kullanarak kaynak ilişkilendirmesini kaldırmak <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> veya <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="22dff-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="22dff-108">Kaynak ile yeni bir günlük kaydedin.</span><span class="sxs-lookup"><span data-stu-id="22dff-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22dff-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22dff-109">See Also</span></span>  
 [<span data-ttu-id="22dff-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="22dff-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

