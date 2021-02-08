---
description: 'Hakkında daha fazla bilgi edinin: uygulamadan bilgileri günlüğe kaydetme (Visual Basic)'
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
ms.openlocfilehash: 6e0adf45c12d98c8bc6d177d85accf9bee347f75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775077"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="e18f9-103">Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e18f9-103">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="e18f9-104">Bu bölüm, veya nesnesini kullanarak uygulamanızdaki bilgilerin nasıl günlüğe alınacağını `My.Application.Log` `My.Log` ve uygulamanın günlüğe kaydetme yeteneklerini genişletmeyi kapsayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="e18f9-104">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="e18f9-105">`Log`Nesnesi, uygulamanın günlük dinleyicilerine bilgi yazma yöntemleri sağlar ve `Log` nesnenin Gelişmiş `TraceSource` özelliği ayrıntılı yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e18f9-105">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="e18f9-106">`Log`Nesne, uygulamanın yapılandırma dosyası tarafından yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e18f9-106">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="e18f9-107">`My.Log`Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e18f9-107">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="e18f9-108">İstemci uygulamaları için kullanın `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e18f9-108">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="e18f9-109">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="e18f9-109">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="e18f9-110">Görevler</span><span class="sxs-lookup"><span data-stu-id="e18f9-110">Tasks</span></span>  
  
|<span data-ttu-id="e18f9-111">Amaç</span><span class="sxs-lookup"><span data-stu-id="e18f9-111">To</span></span>|<span data-ttu-id="e18f9-112">Bkz.</span><span class="sxs-lookup"><span data-stu-id="e18f9-112">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="e18f9-113">Olay bilgilerini uygulamanın günlüklerine yazın.</span><span class="sxs-lookup"><span data-stu-id="e18f9-113">Write event information to the application's logs.</span></span>|[<span data-ttu-id="e18f9-114">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="e18f9-114">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)|  
|<span data-ttu-id="e18f9-115">Özel durum bilgilerini uygulamanın günlüklerine yazın.</span><span class="sxs-lookup"><span data-stu-id="e18f9-115">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="e18f9-116">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e18f9-116">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)|  
|<span data-ttu-id="e18f9-117">Uygulama başlatıldığında ve kapandığında izleme bilgilerini uygulamanın günlüklerine yazın.</span><span class="sxs-lookup"><span data-stu-id="e18f9-117">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="e18f9-118">Nasıl yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e18f9-118">How to: Log Messages When the Application Starts or Shuts Down</span></span>](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="e18f9-119">`My.Application.Log`Bir metin dosyasına bilgi yazmak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e18f9-119">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="e18f9-120">Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma</span><span class="sxs-lookup"><span data-stu-id="e18f9-120">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="e18f9-121">`My.Application.Log`Bir olay günlüğüne bilgi yazmak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e18f9-121">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="e18f9-122">Nasıl yapılır: Uygulama Olay Günlüğüne Yazma</span><span class="sxs-lookup"><span data-stu-id="e18f9-122">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="e18f9-123">Yazma bilgilerinin bulunduğu yeri değiştirin `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e18f9-123">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="e18f9-124">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e18f9-124">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="e18f9-125">Nerede `My.Application.Log` yazma bilgileri belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e18f9-125">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="e18f9-126">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="e18f9-126">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="e18f9-127">İçin özel bir günlük dinleyicisi oluşturun `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e18f9-127">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="e18f9-128">İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e18f9-128">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="e18f9-129">Günlüklerin çıkışını filtreleyin `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e18f9-129">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="e18f9-130">İzlenecek yol: My.Application.Log Çıktısını Filtreleme</span><span class="sxs-lookup"><span data-stu-id="e18f9-130">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="e18f9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e18f9-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="e18f9-132">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="e18f9-132">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="e18f9-133">Sorun Giderme: Günlük Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="e18f9-133">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
