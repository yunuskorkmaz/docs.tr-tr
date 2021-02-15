---
description: "Hakkında daha fazla bilgi edinin: EventLogSource 'ta belirtilen kaynak adı, EventLogName içinde belirtilenden farklı bir günlüğe kayıtlı"
title: EventLogSource 'da belirtilen kaynak adı, EventLogName içinde belirtilenden farklı bir günlüğe kayıtlı
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: d6b9c1265276f94369d37e6ac55604b761fb9bcc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455463"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="0da3e-103">EventLogSource 'da belirtilen kaynak adı, EventLogName içinde belirtilenden farklı bir günlüğe kayıtlı</span><span class="sxs-lookup"><span data-stu-id="0da3e-103">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>

<span data-ttu-id="0da3e-104">, `EventLog` Farklı bir günlüğe kayıtlı bir kaynağa başvurmaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="0da3e-104">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="0da3e-105">Bir olay günlüğüne giriş yazıyorsanız, özelliğini belirtmeniz gerekir <xref:System.Diagnostics.EventLog.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="0da3e-105">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="0da3e-106"><xref:System.Diagnostics.EventLog.Source%2A>Özelliği, bileşenini olay günlüğüne geçerli bir giriş kaynağı olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0da3e-106">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="0da3e-107">Tek bir kaynak, aynı anda yalnızca bir olay günlüğü ile ilişkilendirilebilir (ve bu nedenle girdileri yazılabilir).</span><span class="sxs-lookup"><span data-stu-id="0da3e-107">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="0da3e-108">Varsayılan olarak, ilk olarak bileşeninizi geçerli bir kaynak olarak kaydettirmeden bir girdi yazmaya çalışırsanız, sistem, kaynak dize olarak özelliğin değerini kullanarak kaynağı otomatik olarak olay günlüğüne kaydeder <xref:System.Diagnostics.EventLog.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="0da3e-108">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0da3e-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0da3e-109">To correct this error</span></span>  
  
- <span data-ttu-id="0da3e-110">Kaynağın doğru günlüğe kaydedildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0da3e-110">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="0da3e-111">Bunu yapmak için, <xref:System.Diagnostics.EventLog.CreateEventSource%2A> uygulamanızı olay günlüğüne benzersiz bir şekilde tanımlayan bir dize belirtmek için yöntemini veya aşırı yüklemelerinin birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0da3e-111">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da3e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0da3e-112">See also</span></span>

- <span data-ttu-id="0da3e-113">[Olay günlüklerini yönetme](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0da3e-113">[Administering Event Logs](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="0da3e-114">[Olay günlüğü başvuruları](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0da3e-114">[Event Log References](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span></span>
- <span data-ttu-id="0da3e-115">[Nasıl yapılır: uygulamanızı olay günlüğü girdilerinin kaynağı olarak ekleme](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0da3e-115">[How to: Add Your Application as a Source of Event Log Entries](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span></span>
- <span data-ttu-id="0da3e-116">[Nasıl yapılır: olay kaynağını kaldırma](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0da3e-116">[How to: Remove an Event Source](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span></span>
