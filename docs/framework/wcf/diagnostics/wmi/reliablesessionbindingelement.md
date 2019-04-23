---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: b0a621da43402777cc620f1876bd968a72bb8c12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973115"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="0110d-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="0110d-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="0110d-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="0110d-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0110d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0110d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="0110d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0110d-105">Methods</span></span>  
 <span data-ttu-id="0110d-106">ReliableSessionBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="0110d-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0110d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0110d-107">Properties</span></span>  
 <span data-ttu-id="0110d-108">ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0110d-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="0110d-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="0110d-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="0110d-110">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="0110d-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="0110d-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-112">Bir hedef fabrikası tarafından oluşturulan güvenilir kanalda ileti kaynağı için bir onay göndermeden önce bekleyeceği zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="0110d-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="0110d-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="0110d-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="0110d-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="0110d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="0110d-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-116">Akış denetimi etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0110d-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="0110d-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="0110d-117">InactivityTimeout</span></span>  
 <span data-ttu-id="0110d-118">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="0110d-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="0110d-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-120">Herhangi bir ileti kanalı hatalı önce göndermemeyi diğer tarafın kanalı göndermemesini sağladığı sürenin üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0110d-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="0110d-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="0110d-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="0110d-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="0110d-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="0110d-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-124">Bekleyebilen kabul edilecek bekleyebileceği kanalları maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="0110d-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="0110d-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="0110d-125">MaxRetryCount</span></span>  
 <span data-ttu-id="0110d-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="0110d-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="0110d-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-128">En fazla kaç kez güvenilir bir kanalın çalışır değil aldığı için bir bildirim çağırarak bir ileti göndermesi `Send` , arka plandaki kanal.</span><span class="sxs-lookup"><span data-stu-id="0110d-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="0110d-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="0110d-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="0110d-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="0110d-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="0110d-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-132">Güvenilir oturum için maksimum aktarım pencere boyutu.</span><span class="sxs-lookup"><span data-stu-id="0110d-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="0110d-133">Sıralı</span><span class="sxs-lookup"><span data-stu-id="0110d-133">Ordered</span></span>  
 <span data-ttu-id="0110d-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="0110d-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="0110d-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-136">İletilerin gönderildiği sırada ulşamasını garanti edilip edilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0110d-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="0110d-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="0110d-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="0110d-138">Veri türü: tamsayı</span><span class="sxs-lookup"><span data-stu-id="0110d-138">Data type: integer</span></span>  
  
 <span data-ttu-id="0110d-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0110d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0110d-140">Güvenilir bir oturumda kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0110d-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0110d-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0110d-141">Requirements</span></span>  
  
|<span data-ttu-id="0110d-142">MOF</span><span class="sxs-lookup"><span data-stu-id="0110d-142">MOF</span></span>|<span data-ttu-id="0110d-143">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0110d-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0110d-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="0110d-144">Namespace</span></span>|<span data-ttu-id="0110d-145">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0110d-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0110d-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0110d-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
