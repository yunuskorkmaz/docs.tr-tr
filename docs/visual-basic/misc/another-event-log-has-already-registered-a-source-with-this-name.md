---
description: 'Daha fazla bilgi edinin: başka bir olay günlüğü zaten bu adı taşıyan bir kaynağı kaydetti'
title: Başka bir olay günlüğü bu adı taşıyan bir kaynağı zaten kaydetti
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: ec6ae0b3ef12452a0135e5bf17dbdd5844c0f478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787363"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="e8bdb-103">Başka bir olay günlüğü bu adı taşıyan bir kaynağı zaten kaydetti</span><span class="sxs-lookup"><span data-stu-id="e8bdb-103">Another event log has already registered a source with this name</span></span>

<span data-ttu-id="e8bdb-104">Belirtilen kaynağın başka bir olay günlüğü ile kaydedildiği bir olay günlüğüne giriş yazma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="e8bdb-104">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="e8bdb-105"><xref:System.Diagnostics.EventLog.Source%2A> <xref:System.Diagnostics.EventLog> Bileşeninizin bir günlüğe giriş yazmadan önce bileşen örneğinizin özelliğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8bdb-105">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="e8bdb-106">Bu durumda, sistem belirttiğiniz kaynağın, bileşenin yazıldığı olay günlüğüne kaydedilip kullanmadığını denetler ve <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekirse çağırır.</span><span class="sxs-lookup"><span data-stu-id="e8bdb-106">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e8bdb-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e8bdb-107">To correct this error</span></span>  
  
1. <span data-ttu-id="e8bdb-108">Kaynak ilişkilendirmesini, veya yöntemini kullanarak ilk günlük ile kaldırın <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> .</span><span class="sxs-lookup"><span data-stu-id="e8bdb-108">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2. <span data-ttu-id="e8bdb-109">Kaynağı yeni günlüğe kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e8bdb-109">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8bdb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8bdb-110">See also</span></span>

- [<span data-ttu-id="e8bdb-111">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="e8bdb-111">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
