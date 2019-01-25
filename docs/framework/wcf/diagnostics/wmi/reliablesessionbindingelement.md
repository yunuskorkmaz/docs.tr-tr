---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: adf7d8958e2361d6e26576f6b20321b9c5666d1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688889"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="35bff-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="35bff-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="35bff-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="35bff-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35bff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35bff-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="35bff-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="35bff-105">Methods</span></span>  
 <span data-ttu-id="35bff-106">ReliableSessionBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="35bff-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="35bff-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="35bff-107">Properties</span></span>  
 <span data-ttu-id="35bff-108">ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="35bff-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="35bff-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="35bff-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="35bff-110">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="35bff-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="35bff-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-112">Bir hedef fabrikası tarafından oluşturulan güvenilir kanalda ileti kaynağı için bir onay göndermeden önce bekleyeceği zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="35bff-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="35bff-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="35bff-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="35bff-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="35bff-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="35bff-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-116">Akış denetimi etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="35bff-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="35bff-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="35bff-117">InactivityTimeout</span></span>  
 <span data-ttu-id="35bff-118">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="35bff-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="35bff-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-120">Herhangi bir ileti kanalı hatalı önce göndermemeyi diğer tarafın kanalı göndermemesini sağladığı sürenin üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35bff-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="35bff-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="35bff-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="35bff-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="35bff-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="35bff-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-124">Bekleyebilen kabul edilecek bekleyebileceği kanalları maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="35bff-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="35bff-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="35bff-125">MaxRetryCount</span></span>  
 <span data-ttu-id="35bff-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="35bff-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="35bff-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-128">En fazla kaç kez güvenilir bir kanalın çalışır değil aldığı için bir bildirim çağırarak bir ileti göndermesi `Send` , arka plandaki kanal.</span><span class="sxs-lookup"><span data-stu-id="35bff-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="35bff-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="35bff-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="35bff-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="35bff-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="35bff-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-132">Güvenilir oturum için maksimum aktarım pencere boyutu.</span><span class="sxs-lookup"><span data-stu-id="35bff-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="35bff-133">Sıralı</span><span class="sxs-lookup"><span data-stu-id="35bff-133">Ordered</span></span>  
 <span data-ttu-id="35bff-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="35bff-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="35bff-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-136">İletilerin gönderildiği sırada ulşamasını garanti edilip edilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="35bff-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="35bff-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="35bff-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="35bff-138">Veri türü: tamsayı</span><span class="sxs-lookup"><span data-stu-id="35bff-138">Data type: integer</span></span>  
  
 <span data-ttu-id="35bff-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="35bff-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="35bff-140">Güvenilir bir oturumda kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="35bff-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35bff-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35bff-141">Requirements</span></span>  
  
|<span data-ttu-id="35bff-142">MOF</span><span class="sxs-lookup"><span data-stu-id="35bff-142">MOF</span></span>|<span data-ttu-id="35bff-143">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="35bff-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="35bff-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="35bff-144">Namespace</span></span>|<span data-ttu-id="35bff-145">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="35bff-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35bff-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35bff-146">See also</span></span>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
