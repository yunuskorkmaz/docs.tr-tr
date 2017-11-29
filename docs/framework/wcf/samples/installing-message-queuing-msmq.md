---
title: "İleti Kuyruğa Alma Yükleme (MSMQ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 89d81a25da6494fc9cbf041ae68f2985b5c90a81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="8c74f-102">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="8c74f-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="8c74f-103">Aşağıdaki yordamlar, Message Queuing 4.0 ve Message Queuing 3.0 nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c74f-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c74f-104">Message Queuing 4.0 kullanılabilir değil [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c74f-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="8c74f-105">Windows Server 2008 veya Windows Server 2008 R2 üzerinde Message Queuing 4.0 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="8c74f-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="8c74f-106">Sunucu Yöneticisi'nde **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-106">In Server Manager, click **Features**.</span></span>  
  
2.  <span data-ttu-id="8c74f-107">Sağ bölmede altında **Özellik Özeti**, tıklatın **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3.  <span data-ttu-id="8c74f-108">Sonuçta elde edilen penceresinde **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4.  <span data-ttu-id="8c74f-109">Genişletme **Message Queuing Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-109">Expand **Message Queuing Services**.</span></span>  
  
5.  <span data-ttu-id="8c74f-110">Tıklatın **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için), ardından **HTTP desteği**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6.  <span data-ttu-id="8c74f-111">Tıklatın **sonraki**, ardından **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="8c74f-112">Message Queuing 4.0, Windows 7 veya Windows Vista'yı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="8c74f-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1.  <span data-ttu-id="8c74f-113">Açık **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-113">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="8c74f-114">Tıklatın **programları** ve ardından, **programlar ve Özellikler**, tıklatın **Windows özelliklerini açma ve kapatma**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3.  <span data-ttu-id="8c74f-115">Microsoft Message Queue (MSMQ) sunucusu genişletin, Microsoft Message Queue (MSMQ) Sunucu Çekirdeği'ni genişletin ve ardından yüklemek aşağıdaki olan Message Queuing özelliklerin onay kutularını seçin:</span><span class="sxs-lookup"><span data-stu-id="8c74f-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    -   <span data-ttu-id="8c74f-116">MSMQ Active Directory etki alanı Hizmetleri Tümleştirme (bir etki alanına katılmış bilgisayarlar için).</span><span class="sxs-lookup"><span data-stu-id="8c74f-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    -   <span data-ttu-id="8c74f-117">MSMQ HTTP desteği.</span><span class="sxs-lookup"><span data-stu-id="8c74f-117">MSMQ HTTP Support.</span></span>  
  
4.  <span data-ttu-id="8c74f-118">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="8c74f-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="8c74f-119">Bilgisayarı yeniden başlatmanız istenirse, tıklatın **Tamam** yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="8c74f-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="8c74f-120">Windows XP ve Windows Server 2003'te Message Queuing 3.0 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="8c74f-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="8c74f-121">Açık **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-121">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="8c74f-122">Tıklatın **Program Ekle/Kaldır** ve ardından **Windows Bileşenleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3.  <span data-ttu-id="8c74f-123">Message Queuing seçin ve tıklatın **ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c74f-124">Çalıştırıyorsanız, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Message Queuing erişmek için uygulama sunucusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="8c74f-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4.  <span data-ttu-id="8c74f-125">MSMQ HTTP desteği Ayrıntıları sayfasında seçilen seçeneği emin olun.</span><span class="sxs-lookup"><span data-stu-id="8c74f-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5.  <span data-ttu-id="8c74f-126">Tıklatın **Tamam** Ayrıntılar sayfası çıkın ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="8c74f-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="8c74f-127">Yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="8c74f-127">Complete the installation.</span></span>  
  
6.  <span data-ttu-id="8c74f-128">Bilgisayarı yeniden başlatmanız istenirse, tıklatın **Tamam** yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="8c74f-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c74f-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c74f-129">See Also</span></span>  
 [<span data-ttu-id="8c74f-130">Kurulum yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8c74f-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
