---
title: İleti Kuyruğa Alma Yükleme (MSMQ)
description: Bir kerelik Kurulum yordamının bir parçası olarak WFC örnekleri ile kullanmak üzere 4,0 Message Queuing ve Message Queuing 3,0 ' i nasıl yükleyeceğinizi öğrenin.
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: bf33a5cd899bf2d7ef4947c51ac1723c8eb80c29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281878"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="671e1-103">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="671e1-103">Installing Message Queuing (MSMQ)</span></span>

<span data-ttu-id="671e1-104">Aşağıdaki yordamlarda Message Queuing 4,0 ve Message Queuing 3,0 ' nin nasıl yükleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="671e1-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="671e1-105">Message Queuing 4,0, Windows XP ve Windows Server 2003 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="671e1-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="671e1-106">Message Queuing 4,0 ' i Windows Server 2008 veya Windows Server 2008 R2 'ye yüklemek için</span><span class="sxs-lookup"><span data-stu-id="671e1-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="671e1-107">Sunucu Yöneticisi, **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="671e1-108">Sağ bölmedeki **Özellikler Özeti**' ne tıklayın, **Özellik Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="671e1-109">Ortaya çıkan pencerede **Message Queuing**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="671e1-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="671e1-110">**Message Queuing Hizmetleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="671e1-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="671e1-111">**Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) öğesine tıklayın ve ardından **http desteği**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="671e1-112">**İleri**' ye ve ardından **Install**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="671e1-113">Windows 7 veya Windows Vista 'da Message Queuing 4,0 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="671e1-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="671e1-114">**Denetim Masası 'nı** açın.</span><span class="sxs-lookup"><span data-stu-id="671e1-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="671e1-115">**Programlar** ' a ve ardından **Programlar ve Özellikler**' ın altında, **Windows özelliklerini aç ve Kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="671e1-116">Microsoft Message Queue (MSMQ) sunucusu ' nu genişletin, Microsoft Message Queue (MSMQ) Server Core ' u genişletin ve ardından yüklemek üzere aşağıdaki Message Queuing Özellikler onay kutularını seçin:</span><span class="sxs-lookup"><span data-stu-id="671e1-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="671e1-117">MSMQ Active Directory Domain Services Tümleştirme (bir etki alanına katılmış bilgisayarlar için).</span><span class="sxs-lookup"><span data-stu-id="671e1-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="671e1-118">MSMQ HTTP desteği.</span><span class="sxs-lookup"><span data-stu-id="671e1-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="671e1-119">**Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="671e1-120">Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="671e1-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="671e1-121">Message Queuing 3,0 ' i Windows XP ve Windows Server 2003 ' ye yüklemek için</span><span class="sxs-lookup"><span data-stu-id="671e1-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="671e1-122">**Denetim Masası 'nı** açın.</span><span class="sxs-lookup"><span data-stu-id="671e1-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="671e1-123">**Program Ekle Kaldır** ' a ve ardından **Windows Bileşenleri Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="671e1-124">Message Queuing seçin ve **Ayrıntılar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="671e1-125">Windows Server 2003 çalıştırıyorsanız, Message Queuing erişmek için uygulama sunucusu ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="671e1-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="671e1-126">Ayrıntılar sayfasında MSMQ HTTP desteği seçeneğinin seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="671e1-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="671e1-127">Ayrıntılar sayfasından çıkmak için **Tamam** ' ı tıklatın ve ardından **İleri**' yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="671e1-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="671e1-128">Yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="671e1-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="671e1-129">Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="671e1-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671e1-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="671e1-130">See also</span></span>

- [<span data-ttu-id="671e1-131">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="671e1-131">Set-Up Instructions</span></span>](set-up-instructions.md)
