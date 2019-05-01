---
title: İleti Kuyruğa Alma Yükleme (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 64736f8f0a34a53658dd2838738a3d36b3891d2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954953"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="69471-102">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="69471-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="69471-103">Aşağıdaki yordamlar, Message Queuing 4.0 ve Message Queuing 3.0 nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="69471-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69471-104">Message Queuing 4.0 kullanılabilir değil [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69471-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="69471-105">Message Queuing 4.0, Windows Server 2008 veya Windows Server 2008 R2 üzerinde yükleme için</span><span class="sxs-lookup"><span data-stu-id="69471-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="69471-106">Sunucu Yöneticisi'nde **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="69471-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="69471-107">Sağ bölmede **özellikler özeti**, tıklayın **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="69471-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="69471-108">Sonuçta elde edilen penceresinde **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="69471-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="69471-109">Genişletin **Message Queuing Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="69471-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="69471-110">Tıklayın **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için),'ı **HTTP desteği**.</span><span class="sxs-lookup"><span data-stu-id="69471-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="69471-111">Tıklayın **sonraki**, ardından **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="69471-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="69471-112">Message Queuing 4.0, Windows 7 veya Windows Vista'yı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="69471-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="69471-113">**Denetim Masası**'nı açın.</span><span class="sxs-lookup"><span data-stu-id="69471-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="69471-114">Tıklayın **programlar** ve sonra **programlar ve Özellikler**, tıklayın **Windows özelliklerini açma ve kapatma**.</span><span class="sxs-lookup"><span data-stu-id="69471-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="69471-115">Microsoft Message Queue (MSMQ) sunucusunu genişletin, Microsoft Message Queue (MSMQ) Sunucu Çekirdeği'ni genişletin ve sonra yüklemek aşağıdaki olan Message Queuing özellikler için onay kutularını seçin:</span><span class="sxs-lookup"><span data-stu-id="69471-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="69471-116">MSMQ Active Directory etki alanı Hizmetleri Tümleştirme (bir etki alanına katılmış bilgisayarlar için).</span><span class="sxs-lookup"><span data-stu-id="69471-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="69471-117">MSMQ HTTP desteği.</span><span class="sxs-lookup"><span data-stu-id="69471-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="69471-118">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="69471-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="69471-119">Bilgisayarı yeniden başlatmanız istenirse, tıklayın **Tamam** yüklemeyi tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="69471-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="69471-120">Message Queuing 3.0, Windows XP ve Windows Server 2003'te yüklemek için</span><span class="sxs-lookup"><span data-stu-id="69471-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="69471-121">**Denetim Masası**'nı açın.</span><span class="sxs-lookup"><span data-stu-id="69471-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="69471-122">Tıklayın **Program Ekle/Kaldır** ve ardından **Windows BileşenleriEkle/**.</span><span class="sxs-lookup"><span data-stu-id="69471-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="69471-123">Message Queuing seçip tıklayın **ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="69471-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69471-124">Çalıştırıyorsanız [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Message Queuing erişmek için uygulama sunucusu seçin.</span><span class="sxs-lookup"><span data-stu-id="69471-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="69471-125">MSMQ HTTP desteği, Ayrıntılar sayfasında belirlenen seçenek emin olun.</span><span class="sxs-lookup"><span data-stu-id="69471-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="69471-126">Tıklayın **Tamam** Ayrıntılar sayfası çıkın ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="69471-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="69471-127">Yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="69471-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="69471-128">Bilgisayarı yeniden başlatmanız istenirse, tıklayın **Tamam** yüklemeyi tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="69471-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69471-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69471-129">See also</span></span>

- [<span data-ttu-id="69471-130">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="69471-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
