---
title: "EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c190caa7634760c2e4dc4a2bb7a9a09f532eb0ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="c6bfb-102">EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir</span><span class="sxs-lookup"><span data-stu-id="c6bfb-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="c6bfb-103">`EventLog` Farklı günlüğe kayıtlı bir kaynak başvurmak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="c6bfb-104">Girişler için olay günlüğünü yazdığınız varsa, belirtmeniz gerekir <xref:System.Diagnostics.EventLog.Source%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="c6bfb-105"><xref:System.Diagnostics.EventLog.Source%2A> Özelliği olay günlüğüyle bileşeniniz giriş geçerli bir kaynak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="c6bfb-106">Tek bir kaynak ilişkilendirilmesi (ve bu nedenle girişlere yazma) aynı anda yalnızca bir olay günlüğü.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="c6bfb-107">Kaynak ve olay günlüğüne kaydeder ilk bileşeniniz, sistem gibi geçerli bir kaynak otomatik olarak kayıtlı olmayan bir giriş yazmak çalışırsanız, varsayılan olarak, değeri kullanılarak <xref:System.Diagnostics.EventLog.Source%2A> özelliği kaynak dizesi olarak.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6bfb-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c6bfb-108">To correct this error</span></span>  
  
-   <span data-ttu-id="c6bfb-109">Kaynak doğru günlüğe kayıtlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="c6bfb-110">Bunu yapmak için kullanın <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metodunu ya kendi aşırı bileşeniniz olay günlüğüne benzersiz olarak tanımlayan bir dize belirtin.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6bfb-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6bfb-111">See Also</span></span>  
 [<span data-ttu-id="c6bfb-112">Olay günlüklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="c6bfb-112">Administering Event Logs</span></span>](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="c6bfb-113">Olay günlüğü başvuruları</span><span class="sxs-lookup"><span data-stu-id="c6bfb-113">Event Log References</span></span>](http://msdn.microsoft.com/en-us/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [<span data-ttu-id="c6bfb-114">Nasıl yapılır: olay günlüğü girişleri kaynağı olarak, uygulamanızın ekleyin</span><span class="sxs-lookup"><span data-stu-id="c6bfb-114">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)  
 [<span data-ttu-id="c6bfb-115">Nasıl yapılır: bir olay kaynağı Kaldır</span><span class="sxs-lookup"><span data-stu-id="c6bfb-115">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)
