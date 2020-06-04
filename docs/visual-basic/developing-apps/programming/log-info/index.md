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
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410029"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="e1726-102">Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1726-102">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="e1726-103">Bu bölüm, veya nesnesini kullanarak uygulamanızdaki bilgilerin nasıl günlüğe alınacağını `My.Application.Log` `My.Log` ve uygulamanın günlüğe kaydetme yeteneklerini genişletmeyi kapsayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="e1726-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="e1726-104">`Log`Nesnesi, uygulamanın günlük dinleyicilerine bilgi yazma yöntemleri sağlar ve `Log` nesnenin Gelişmiş `TraceSource` özelliği ayrıntılı yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1726-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="e1726-105">`Log`Nesne, uygulamanın yapılandırma dosyası tarafından yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e1726-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="e1726-106">`My.Log`Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1726-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="e1726-107">İstemci uygulamaları için kullanın `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e1726-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="e1726-108">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="e1726-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="e1726-109">Görevler</span><span class="sxs-lookup"><span data-stu-id="e1726-109">Tasks</span></span>  
  
|<span data-ttu-id="e1726-110">Alıcı</span><span class="sxs-lookup"><span data-stu-id="e1726-110">To</span></span>|<span data-ttu-id="e1726-111">Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1726-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="e1726-112">Olay bilgilerini uygulamanın günlüklerine yazın.</span><span class="sxs-lookup"><span data-stu-id="e1726-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="e1726-113">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="e1726-113">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)|  
|<span data-ttu-id="e1726-114">Özel durum bilgilerini uygulamanın günlüklerine yazın.</span><span class="sxs-lookup"><span data-stu-id="e1726-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="e1726-115">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e1726-115">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)|  
|<span data-ttu-id="e1726-116">Uygulama başlatıldığında ve kapandığında izleme bilgilerini uygulamanın günlüklerine yazın.</span><span class="sxs-lookup"><span data-stu-id="e1726-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="e1726-117">Nasıl yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e1726-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="e1726-118">`My.Application.Log`Bir metin dosyasına bilgi yazmak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e1726-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="e1726-119">Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma</span><span class="sxs-lookup"><span data-stu-id="e1726-119">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="e1726-120">`My.Application.Log`Bir olay günlüğüne bilgi yazmak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e1726-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="e1726-121">Nasıl yapılır: Uygulama Olay Günlüğüne Yazma</span><span class="sxs-lookup"><span data-stu-id="e1726-121">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="e1726-122">Yazma bilgilerinin bulunduğu yeri değiştirin `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e1726-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="e1726-123">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e1726-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="e1726-124">Nerede `My.Application.Log` yazma bilgileri belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e1726-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="e1726-125">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="e1726-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="e1726-126">İçin özel bir günlük dinleyicisi oluşturun `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e1726-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="e1726-127">İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1726-127">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="e1726-128">Günlüklerin çıkışını filtreleyin `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="e1726-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="e1726-129">İzlenecek yol: My.Application.Log Çıktısını Filtreleme</span><span class="sxs-lookup"><span data-stu-id="e1726-129">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="e1726-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1726-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="e1726-131">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="e1726-131">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="e1726-132">Sorun Giderme: Günlük Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="e1726-132">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
