---
title: "Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e52aaf4c26b4fa60ee04d7df6aa96980ebbf491
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="c1aa6-102">Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1aa6-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="c1aa6-103">Bu bölümde, uygulama kullanımından bilgileri günlüğe kaydetmek nasıl ele konuları bulunur `My.Application.Log` veya `My.Log` nesne ve uygulamanın günlüğe kaydetme özellikleri genişletme.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="c1aa6-104">`Log` Nesnesi bilgileri uygulamanın günlük dinleyicileri için yazma yöntemleri sağlar ve `Log` nesnesi Gelişmiş `TraceSource` özelliği ayrıntılı yapılandırma bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="c1aa6-105">`Log` Nesnesi, uygulamanın yapılandırma dosyasına tarafından yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="c1aa6-106">`My.Log` Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="c1aa6-107">İstemci uygulamaları için kullanmak `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="c1aa6-108">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c1aa6-109">Görevler</span><span class="sxs-lookup"><span data-stu-id="c1aa6-109">Tasks</span></span>  
  
|<span data-ttu-id="c1aa6-110">Bitiş</span><span class="sxs-lookup"><span data-stu-id="c1aa6-110">To</span></span>|<span data-ttu-id="c1aa6-111">Bkz. </span><span class="sxs-lookup"><span data-stu-id="c1aa6-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="c1aa6-112">Olay bilgileri uygulamanın günlüklere yazılır.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="c1aa6-113">Nasıl yapılır: günlük iletileri yazma</span><span class="sxs-lookup"><span data-stu-id="c1aa6-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="c1aa6-114">Özel durum bilgileri uygulamanın günlüklere yazılır.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="c1aa6-115">Nasıl yapılır: günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="c1aa6-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="c1aa6-116">Uygulamayı başlatır ve kapandığında izleme bilgilerini uygulamanın günlüklere yazılır.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="c1aa6-117">Nasıl yapılır: uygulama başlatır veya kapanırken iletileri günlüğe</span><span class="sxs-lookup"><span data-stu-id="c1aa6-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="c1aa6-118">Yapılandırma `My.Application.Log` bilgilerini metin dosyasına yazma.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="c1aa6-119">Nasıl yapılır: olay bilgilerini metin dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="c1aa6-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="c1aa6-120">Yapılandırma `My.Application.Log` bilgilerini bir olay günlüğüne yazma.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="c1aa6-121">Nasıl yapılır: uygulama olay günlüğüne yazma</span><span class="sxs-lookup"><span data-stu-id="c1aa6-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="c1aa6-122">Değiştirme nereye `My.Application.Log` bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="c1aa6-123">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="c1aa6-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="c1aa6-124">Nereye belirlemek `My.Application.Log` bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="c1aa6-125">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="c1aa6-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="c1aa6-126">İçin özel günlük dinleyicisi oluşturmak `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="c1aa6-127">İzlenecek yol: Özel günlük dinleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1aa6-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="c1aa6-128">Çıktısını filtre `My.Application.Log` günlükleri.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="c1aa6-129">İzlenecek yol: My.Application.Log çıktısını filtreleme</span><span class="sxs-lookup"><span data-stu-id="c1aa6-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c1aa6-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1aa6-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="c1aa6-131">Uygulama günlükleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="c1aa6-131">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="c1aa6-132">Sorun giderme: Günlük dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="c1aa6-132">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
