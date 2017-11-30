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
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="b6bb5-102">Başka bir olay günlüğü bu ada sahip bir kaynak zaten kaydettirildi</span><span class="sxs-lookup"><span data-stu-id="b6bb5-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="b6bb5-103">Bir olay günlüğüne bir giriş yazmak için belirtilen kaynak ile başka bir olay günlüğü, kayıtlı çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="b6bb5-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="b6bb5-104">Ayarlamalısınız <xref:System.Diagnostics.EventLog.Source%2A> özelliği, <xref:System.Diagnostics.EventLog> bileşeniniz bir giriş bir günlük dosyasına yazar önce bileşen örneği.</span><span class="sxs-lookup"><span data-stu-id="b6bb5-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="b6bb5-105">Bu durumda, sistem, belirtilen kaynak bileşeni yazma olay günlüğü ve çağrıları ile kaydedildiğini denetler <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="b6bb5-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6bb5-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b6bb5-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b6bb5-107">İlk günlük kullanarak kaynak ilişkilendirmesini kaldırmak <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> veya <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6bb5-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="b6bb5-108">Kaynak ile yeni bir günlük kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b6bb5-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bb5-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6bb5-109">See Also</span></span>  
 [<span data-ttu-id="b6bb5-110">My.Application.Log nesnesi</span><span class="sxs-lookup"><span data-stu-id="b6bb5-110">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="b6bb5-111">Nasıl yapılır: bir olay kaynağı Kaldır</span><span class="sxs-lookup"><span data-stu-id="b6bb5-111">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [<span data-ttu-id="b6bb5-112">Nasıl yapılır: olay günlüğü girişleri kaynağı olarak, uygulamanızın ekleyin</span><span class="sxs-lookup"><span data-stu-id="b6bb5-112">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
