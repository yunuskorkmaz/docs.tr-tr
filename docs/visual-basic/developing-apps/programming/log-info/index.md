---
title: Uygulamadan Günlüğe Bilgi Kaydetme
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: dace4bac3bf7529b8c50a492a092ad478f4d9e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353249"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="c9e58-102">Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9e58-102">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="c9e58-103">Bu bölümde, uygulamanızdan `My.Application.Log` gelen bilgilerin veya `My.Log` nesnenin nasıl günlüğe kaydedilen bilgilerin nasıl günlüğe kaydedilen ve uygulamanın günlüğe kaydetme yeteneklerinin nasıl genişletilen konular yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9e58-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="c9e58-104">Nesne, `Log` uygulamanın günlük dinleyicilerine bilgi yazmak için yöntemler `Log` sağlar ve `TraceSource` nesnenin gelişmiş özelliği ayrıntılı yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e58-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="c9e58-105">Nesne, `Log` uygulamanın yapılandırma dosyası tarafından yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c9e58-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="c9e58-106">Nesne `My.Log` yalnızca ASP.NET uygulamalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9e58-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="c9e58-107">İstemci uygulamaları `My.Application.Log`için.</span><span class="sxs-lookup"><span data-stu-id="c9e58-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="c9e58-108">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="c9e58-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c9e58-109">Görevler</span><span class="sxs-lookup"><span data-stu-id="c9e58-109">Tasks</span></span>  
  
|<span data-ttu-id="c9e58-110">Alıcı</span><span class="sxs-lookup"><span data-stu-id="c9e58-110">To</span></span>|<span data-ttu-id="c9e58-111">Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9e58-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="c9e58-112">Etkinlik bilgilerini uygulamanın günlüklerine yazın.</span><span class="sxs-lookup"><span data-stu-id="c9e58-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="c9e58-113">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="c9e58-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="c9e58-114">Uygulamanın günlüklerine özel durum bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="c9e58-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="c9e58-115">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="c9e58-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="c9e58-116">Uygulama başlatıldığında ve kapandığında uygulamanın günlüklerine izleme bilgileri yazın.</span><span class="sxs-lookup"><span data-stu-id="c9e58-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="c9e58-117">Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="c9e58-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="c9e58-118">Bir `My.Application.Log` metin dosyasına bilgi yazmak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="c9e58-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="c9e58-119">Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma</span><span class="sxs-lookup"><span data-stu-id="c9e58-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="c9e58-120">Bir `My.Application.Log` olay günlüğüne bilgi yazmak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="c9e58-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="c9e58-121">Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma</span><span class="sxs-lookup"><span data-stu-id="c9e58-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="c9e58-122">Bilgi `My.Application.Log` nin nerede yazacağını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c9e58-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="c9e58-123">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c9e58-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="c9e58-124">Bilgileri `My.Application.Log` nerede yazacağını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c9e58-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="c9e58-125">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="c9e58-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="c9e58-126">Için `My.Application.Log`özel bir günlük dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9e58-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="c9e58-127">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9e58-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="c9e58-128">Günlüklerin çıktısını `My.Application.Log` filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="c9e58-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="c9e58-129">İzlenecek Yol: My.Application.Log Çıktısını Filtreleme</span><span class="sxs-lookup"><span data-stu-id="c9e58-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c9e58-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9e58-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="c9e58-131">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="c9e58-131">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="c9e58-132">Sorun Giderme: Günlük Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c9e58-132">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
