---
title: ReliableSessionBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35a8a92ca93525c9f04ab984073ca64188f03284
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="a73c8-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="a73c8-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="a73c8-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="a73c8-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a73c8-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a73c8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a73c8-105">Methods</span></span>  
 <span data-ttu-id="a73c8-106">ReliableSessionBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="a73c8-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a73c8-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a73c8-107">Properties</span></span>  
 <span data-ttu-id="a73c8-108">ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a73c8-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="a73c8-109">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="a73c8-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="a73c8-110">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="a73c8-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="a73c8-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-112">Bir hedef fabrikada oluşturulan güvenilir kanalda ileti kaynağına onay göndermeden önce bekleyeceği zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="a73c8-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="a73c8-113">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="a73c8-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="a73c8-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="a73c8-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a73c8-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-116">Akış denetimi etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a73c8-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="a73c8-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="a73c8-117">InactivityTimeout</span></span>  
 <span data-ttu-id="a73c8-118">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="a73c8-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="a73c8-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-120">Herhangi bir ileti kanalı hatalı önce göndermemeyi diğer tarafın kanalı göndermemesini en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a73c8-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="a73c8-121">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="a73c8-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="a73c8-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="a73c8-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="a73c8-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-124">Kabul edilmesi için dinleyici bekleyebilirsiniz kanal maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="a73c8-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="a73c8-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="a73c8-125">MaxRetryCount</span></span>  
 <span data-ttu-id="a73c8-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="a73c8-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="a73c8-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-128">Güvenilir bir kanal değil aldığı için bir bildirim arayarak bir ileti yeniden ilettiği için kaç deneme sayısı `Send` temel kanalda.</span><span class="sxs-lookup"><span data-stu-id="a73c8-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="a73c8-129">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="a73c8-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="a73c8-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="a73c8-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="a73c8-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-132">Güvenilir oturum maksimum aktarım pencere boyutu.</span><span class="sxs-lookup"><span data-stu-id="a73c8-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="a73c8-133">sıralı</span><span class="sxs-lookup"><span data-stu-id="a73c8-133">Ordered</span></span>  
 <span data-ttu-id="a73c8-134">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="a73c8-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="a73c8-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-136">İletileri gönderildikleri sırayla gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a73c8-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="a73c8-137">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="a73c8-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="a73c8-138">Veri türü: tamsayı</span><span class="sxs-lookup"><span data-stu-id="a73c8-138">Data type: integer</span></span>  
  
 <span data-ttu-id="a73c8-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a73c8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a73c8-140">Güvenilir oturum sırasında kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a73c8-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a73c8-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a73c8-141">Requirements</span></span>  
  
|<span data-ttu-id="a73c8-142">MOF</span><span class="sxs-lookup"><span data-stu-id="a73c8-142">MOF</span></span>|<span data-ttu-id="a73c8-143">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a73c8-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a73c8-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a73c8-144">Namespace</span></span>|<span data-ttu-id="a73c8-145">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a73c8-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a73c8-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a73c8-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
