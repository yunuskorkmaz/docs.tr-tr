---
title: İleti Kuyruğa Alma Yükleme (MSMQ)
description: Bir kerelik Kurulum yordamının bir parçası olarak WFC örnekleri ile kullanmak üzere 4,0 Message Queuing ve Message Queuing 3,0 ' i nasıl yükleyeceğinizi öğrenin.
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 0d0cb87b40b1cb11eb7692c2fa1e890ec815b13d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244471"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="6695e-103">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="6695e-103">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="6695e-104">Aşağıdaki yordamlarda Message Queuing 4,0 ve Message Queuing 3,0 ' nin nasıl yükleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6695e-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6695e-105">Message Queuing 4,0, Windows XP ve Windows Server 2003 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6695e-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="6695e-106">Message Queuing 4,0 ' i Windows Server 2008 veya Windows Server 2008 R2 'ye yüklemek için</span><span class="sxs-lookup"><span data-stu-id="6695e-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="6695e-107">Sunucu Yöneticisi, **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="6695e-108">Sağ bölmedeki **Özellikler Özeti**' ne tıklayın, **Özellik Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="6695e-109">Ortaya çıkan pencerede **Message Queuing**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="6695e-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="6695e-110">**Message Queuing Hizmetleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="6695e-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="6695e-111">**Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) öğesine tıklayın ve ardından **http desteği**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="6695e-112">**İleri**' ye ve ardından **Install**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="6695e-113">Windows 7 veya Windows Vista 'da Message Queuing 4,0 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="6695e-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="6695e-114">**Denetim Masası 'nı**açın.</span><span class="sxs-lookup"><span data-stu-id="6695e-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="6695e-115">**Programlar** ' a ve ardından **Programlar ve Özellikler**' ın altında, **Windows özelliklerini aç ve Kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="6695e-116">Microsoft Message Queue (MSMQ) sunucusu ' nu genişletin, Microsoft Message Queue (MSMQ) Server Core ' u genişletin ve ardından yüklemek üzere aşağıdaki Message Queuing Özellikler onay kutularını seçin:</span><span class="sxs-lookup"><span data-stu-id="6695e-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="6695e-117">MSMQ Active Directory Domain Services Tümleştirme (bir etki alanına katılmış bilgisayarlar için).</span><span class="sxs-lookup"><span data-stu-id="6695e-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="6695e-118">MSMQ HTTP desteği.</span><span class="sxs-lookup"><span data-stu-id="6695e-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="6695e-119">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="6695e-120">Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6695e-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="6695e-121">Message Queuing 3,0 ' i Windows XP ve Windows Server 2003 ' ye yüklemek için</span><span class="sxs-lookup"><span data-stu-id="6695e-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="6695e-122">**Denetim Masası 'nı**açın.</span><span class="sxs-lookup"><span data-stu-id="6695e-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="6695e-123">**Program Ekle Kaldır** ' a ve ardından **Windows Bileşenleri Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="6695e-124">Message Queuing seçin ve **Ayrıntılar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6695e-125">Windows Server 2003 çalıştırıyorsanız, Message Queuing erişmek için uygulama sunucusu ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="6695e-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="6695e-126">Ayrıntılar sayfasında MSMQ HTTP desteği seçeneğinin seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6695e-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="6695e-127">Ayrıntılar sayfasından çıkmak için **Tamam** ' ı tıklatın ve ardından **İleri**' yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6695e-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="6695e-128">Yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="6695e-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="6695e-129">Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6695e-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6695e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6695e-130">See also</span></span>

- [<span data-ttu-id="6695e-131">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6695e-131">Set-Up Instructions</span></span>](set-up-instructions.md)
