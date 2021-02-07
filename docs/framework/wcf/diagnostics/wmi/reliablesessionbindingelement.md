---
description: 'Daha fazla bilgi edinin: ReliableSessionBindingElement'
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 582fd62a8751a31c2834b7d81219a237c9887236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743869"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="9b2dd-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="9b2dd-103">ReliableSessionBindingElement</span></span>

<span data-ttu-id="9b2dd-104">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="9b2dd-104">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b2dd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b2dd-105">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="9b2dd-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9b2dd-106">Methods</span></span>  

 <span data-ttu-id="9b2dd-107">ReliableSessionBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-107">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9b2dd-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9b2dd-108">Properties</span></span>  

 <span data-ttu-id="9b2dd-109">ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9b2dd-109">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="9b2dd-110">Bildiren Gementınterval</span><span class="sxs-lookup"><span data-stu-id="9b2dd-110">AcknowledgementInterval</span></span>  

 <span data-ttu-id="9b2dd-111">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="9b2dd-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="9b2dd-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-113">Bir hedefin, fabrika tarafından oluşturulan güvenilir kanallarda ileti kaynağına bir onay göndermeden önce beklediği zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-113">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="9b2dd-114">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="9b2dd-114">FlowControlEnabled</span></span>  

 <span data-ttu-id="9b2dd-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9b2dd-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="9b2dd-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-117">Akış denetiminin etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-117">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="9b2dd-118">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="9b2dd-118">InactivityTimeout</span></span>  

 <span data-ttu-id="9b2dd-119">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="9b2dd-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="9b2dd-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-121">Kanalın, diğer iletişim tarafına ait diğer tarafın kanaldan önce herhangi bir ileti gönderemediğinden izin verilen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-121">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="9b2dd-122">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="9b2dd-122">MaxPendingChannels</span></span>  

 <span data-ttu-id="9b2dd-123">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="9b2dd-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b2dd-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-125">Dinleyicide kabul edilmesini bekleyebilen kanal sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-125">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="9b2dd-126">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="9b2dd-126">MaxRetryCount</span></span>  

 <span data-ttu-id="9b2dd-127">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="9b2dd-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b2dd-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-129">Güvenilir bir kanalın, kendisi için onay almadığı bir iletiyi kendi temel kanalına çağırarak, en fazla kaç kez yeniden aktarmak için deneme sayısı `Send` .</span><span class="sxs-lookup"><span data-stu-id="9b2dd-129">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="9b2dd-130">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="9b2dd-130">MaxTransferWindowSize</span></span>  

 <span data-ttu-id="9b2dd-131">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="9b2dd-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b2dd-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-133">Güvenilir oturum için en büyük aktarım penceresi boyutu.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-133">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="9b2dd-134">Sipariş edildi</span><span class="sxs-lookup"><span data-stu-id="9b2dd-134">Ordered</span></span>  

 <span data-ttu-id="9b2dd-135">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9b2dd-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="9b2dd-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-137">İletilerin gönderildikleri sırada gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-137">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="9b2dd-138">Belirten ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="9b2dd-138">ReliableMessagingVersion</span></span>  

 <span data-ttu-id="9b2dd-139">Veri türü: tamsayı</span><span class="sxs-lookup"><span data-stu-id="9b2dd-139">Data type: integer</span></span>  
  
 <span data-ttu-id="9b2dd-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9b2dd-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b2dd-141">Güvenilir oturumda kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-141">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b2dd-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b2dd-142">Requirements</span></span>  
  
|<span data-ttu-id="9b2dd-143">MOF</span><span class="sxs-lookup"><span data-stu-id="9b2dd-143">MOF</span></span>|<span data-ttu-id="9b2dd-144">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9b2dd-145">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9b2dd-145">Namespace</span></span>|<span data-ttu-id="9b2dd-146">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="9b2dd-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b2dd-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-147">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
