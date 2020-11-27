---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: f91e38ab88cd9f93e9bec0e3a6ca65254bc49570
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273327"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="b4b72-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="b4b72-102">ReliableSessionBindingElement</span></span>

<span data-ttu-id="b4b72-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="b4b72-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b72-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b4b72-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b4b72-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b4b72-105">Methods</span></span>  

 <span data-ttu-id="b4b72-106">ReliableSessionBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b4b72-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b4b72-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b4b72-107">Properties</span></span>  

 <span data-ttu-id="b4b72-108">ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b4b72-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="b4b72-109">Bildiren Gementınterval</span><span class="sxs-lookup"><span data-stu-id="b4b72-109">AcknowledgementInterval</span></span>  

 <span data-ttu-id="b4b72-110">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="b4b72-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="b4b72-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-112">Bir hedefin, fabrika tarafından oluşturulan güvenilir kanallarda ileti kaynağına bir onay göndermeden önce beklediği zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="b4b72-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="b4b72-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="b4b72-113">FlowControlEnabled</span></span>  

 <span data-ttu-id="b4b72-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b4b72-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4b72-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-116">Akış denetiminin etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="b4b72-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="b4b72-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="b4b72-117">InactivityTimeout</span></span>  

 <span data-ttu-id="b4b72-118">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="b4b72-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="b4b72-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-120">Kanalın, diğer iletişim tarafına ait diğer tarafın kanaldan önce herhangi bir ileti gönderemediğinden izin verilen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4b72-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="b4b72-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="b4b72-121">MaxPendingChannels</span></span>  

 <span data-ttu-id="b4b72-122">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="b4b72-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4b72-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-124">Dinleyicide kabul edilmesini bekleyebilen kanal sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="b4b72-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="b4b72-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="b4b72-125">MaxRetryCount</span></span>  

 <span data-ttu-id="b4b72-126">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="b4b72-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4b72-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-128">Güvenilir bir kanalın, kendisi için onay almadığı bir iletiyi kendi temel kanalına çağırarak, en fazla kaç kez yeniden aktarmak için deneme sayısı `Send` .</span><span class="sxs-lookup"><span data-stu-id="b4b72-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="b4b72-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="b4b72-129">MaxTransferWindowSize</span></span>  

 <span data-ttu-id="b4b72-130">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="b4b72-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4b72-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-132">Güvenilir oturum için en büyük aktarım penceresi boyutu.</span><span class="sxs-lookup"><span data-stu-id="b4b72-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="b4b72-133">Sipariş edildi</span><span class="sxs-lookup"><span data-stu-id="b4b72-133">Ordered</span></span>  

 <span data-ttu-id="b4b72-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b4b72-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4b72-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-136">İletilerin gönderildikleri sırada gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b4b72-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="b4b72-137">Belirten ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="b4b72-137">ReliableMessagingVersion</span></span>  

 <span data-ttu-id="b4b72-138">Veri türü: tamsayı</span><span class="sxs-lookup"><span data-stu-id="b4b72-138">Data type: integer</span></span>  
  
 <span data-ttu-id="b4b72-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4b72-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b72-140">Güvenilir oturumda kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b4b72-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4b72-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4b72-141">Requirements</span></span>  
  
|<span data-ttu-id="b4b72-142">MOF</span><span class="sxs-lookup"><span data-stu-id="b4b72-142">MOF</span></span>|<span data-ttu-id="b4b72-143">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4b72-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b4b72-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b4b72-144">Namespace</span></span>|<span data-ttu-id="b4b72-145">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="b4b72-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4b72-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b72-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
