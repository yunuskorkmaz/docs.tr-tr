---
title: İleti Kuyruğa Alma Yükleme (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 42e66029f8538877ded424f72cb6c829444d1ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935987"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="199ba-102">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="199ba-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="199ba-103">Aşağıdaki yordamlarda Message Queuing 4,0 ve Message Queuing 3,0 ' nin nasıl yükleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="199ba-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="199ba-104">Message Queuing 4,0, ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="199ba-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="199ba-105">Message Queuing 4,0 ' i Windows Server 2008 veya Windows Server 2008 R2 'ye yüklemek için</span><span class="sxs-lookup"><span data-stu-id="199ba-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="199ba-106">Sunucu Yöneticisi, **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="199ba-107">Sağ bölmedeki **Özellikler Özeti**' ne tıklayın, **Özellik Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="199ba-108">Ortaya çıkan pencerede **Message Queuing**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="199ba-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="199ba-109">**Message Queuing Hizmetleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="199ba-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="199ba-110">**Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) öğesine tıklayın ve ardından **http desteği**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="199ba-111">**İleri**' ye ve ardından **Install**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="199ba-112">Windows 7 veya Windows Vista 'da Message Queuing 4,0 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="199ba-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="199ba-113">**Denetim Masası**'nı açın.</span><span class="sxs-lookup"><span data-stu-id="199ba-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="199ba-114">**Programlar** ' a ve ardından **Programlar ve Özellikler**' ın altında, **Windows özelliklerini aç ve Kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="199ba-115">Microsoft Message Queue (MSMQ) sunucusu ' nu genişletin, Microsoft Message Queue (MSMQ) Server Core ' u genişletin ve ardından yüklemek üzere aşağıdaki Message Queuing Özellikler onay kutularını seçin:</span><span class="sxs-lookup"><span data-stu-id="199ba-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="199ba-116">MSMQ Active Directory Domain Services Tümleştirme (bir etki alanına katılmış bilgisayarlar için).</span><span class="sxs-lookup"><span data-stu-id="199ba-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="199ba-117">MSMQ HTTP desteği.</span><span class="sxs-lookup"><span data-stu-id="199ba-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="199ba-118">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="199ba-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="199ba-119">Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="199ba-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="199ba-120">Message Queuing 3,0 ' i Windows XP ve Windows Server 2003 ' ye yüklemek için</span><span class="sxs-lookup"><span data-stu-id="199ba-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="199ba-121">**Denetim Masası**'nı açın.</span><span class="sxs-lookup"><span data-stu-id="199ba-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="199ba-122">**Program Ekle Kaldır** ' a ve ardından **Windows Bileşenleri Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="199ba-123">Message Queuing seçin ve **Ayrıntılar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="199ba-124">Çalıştırıyorsanız [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Message Queuing erişmek için uygulama sunucusu ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="199ba-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="199ba-125">Ayrıntılar sayfasında MSMQ HTTP desteği seçeneğinin seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="199ba-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="199ba-126">Ayrıntılar sayfasından çıkmak için **Tamam** ' ı tıklatın ve ardından **İleri**' yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="199ba-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="199ba-127">Yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="199ba-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="199ba-128">Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="199ba-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199ba-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="199ba-129">See also</span></span>

- [<span data-ttu-id="199ba-130">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="199ba-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
