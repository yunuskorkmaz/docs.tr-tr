---
title: Zaten bir kaynak başka bir olay günlüğü bu ada sahip kayıtlı
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: b32169b79521ec7d0c429e1dce641aca9d747bb1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58032155"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="822de-102">Zaten bir kaynak başka bir olay günlüğü bu ada sahip kayıtlı</span><span class="sxs-lookup"><span data-stu-id="822de-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="822de-103">Bir giriş için bir olay günlüğüne yazmak için burada belirtilen kaynağı başka bir olay günlüğü ile kayıtlı çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="822de-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="822de-104">Ayarlamalısınız <xref:System.Diagnostics.EventLog.Source%2A> özelliği, <xref:System.Diagnostics.EventLog> bileşeniniz girdiyi bir günlük dosyasına yazar. önce bileşen örneği.</span><span class="sxs-lookup"><span data-stu-id="822de-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="822de-105">Bu durumda, sistem, belirtilen kaynak bileşen yazma olay günlüğü ve çağrıları ile kaydedildiğini denetler <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekirse.</span><span class="sxs-lookup"><span data-stu-id="822de-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="822de-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="822de-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="822de-107">İlk günlük kullanarak kaynak ilişkilendirmesini Kaldır <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> veya <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="822de-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="822de-108">Kaynak ile yeni bir günlük kaydedin.</span><span class="sxs-lookup"><span data-stu-id="822de-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="822de-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="822de-109">See also</span></span>

- [<span data-ttu-id="822de-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="822de-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
