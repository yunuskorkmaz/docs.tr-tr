---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2f04e6794342d7bd0acd51481efcbeceb04fd459
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486664"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="de54f-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="de54f-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="de54f-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="de54f-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de54f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de54f-104">Syntax</span></span>  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="de54f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="de54f-105">Methods</span></span>  
 <span data-ttu-id="de54f-106">ReliableSessionBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="de54f-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="de54f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="de54f-107">Properties</span></span>  
 <span data-ttu-id="de54f-108">ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="de54f-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="de54f-109">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="de54f-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="de54f-110">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="de54f-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="de54f-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-112">Bir hedef fabrikada oluşturulan güvenilir kanalda ileti kaynağına onay göndermeden önce bekleyeceği zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="de54f-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="de54f-113">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="de54f-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="de54f-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="de54f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="de54f-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-116">Akış denetimi etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="de54f-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="de54f-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="de54f-117">InactivityTimeout</span></span>  
 <span data-ttu-id="de54f-118">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="de54f-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="de54f-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-120">Herhangi bir ileti kanalı hatalı önce göndermemeyi diğer tarafın kanalı göndermemesini en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="de54f-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="de54f-121">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="de54f-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="de54f-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="de54f-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="de54f-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-124">Kabul edilmesi için dinleyici bekleyebilirsiniz kanal maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="de54f-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="de54f-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="de54f-125">MaxRetryCount</span></span>  
 <span data-ttu-id="de54f-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="de54f-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="de54f-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-128">Güvenilir bir kanal değil aldığı için bir bildirim arayarak bir ileti yeniden ilettiği için kaç deneme sayısı `Send` temel kanalda.</span><span class="sxs-lookup"><span data-stu-id="de54f-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="de54f-129">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="de54f-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="de54f-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="de54f-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="de54f-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-132">Güvenilir oturum maksimum aktarım pencere boyutu.</span><span class="sxs-lookup"><span data-stu-id="de54f-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="de54f-133">sıralı</span><span class="sxs-lookup"><span data-stu-id="de54f-133">Ordered</span></span>  
 <span data-ttu-id="de54f-134">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="de54f-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="de54f-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-136">İletileri gönderildikleri sırayla gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="de54f-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="de54f-137">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="de54f-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="de54f-138">Veri türü: tamsayı</span><span class="sxs-lookup"><span data-stu-id="de54f-138">Data type: integer</span></span>  
  
 <span data-ttu-id="de54f-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="de54f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de54f-140">Güvenilir oturum sırasında kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="de54f-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de54f-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de54f-141">Requirements</span></span>  
  
|<span data-ttu-id="de54f-142">MOF</span><span class="sxs-lookup"><span data-stu-id="de54f-142">MOF</span></span>|<span data-ttu-id="de54f-143">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="de54f-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="de54f-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="de54f-144">Namespace</span></span>|<span data-ttu-id="de54f-145">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="de54f-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de54f-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de54f-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
