---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 3c69b73cc05a56a7556630de0f83675590442293
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274159"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="8a031-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8a031-102">ConnectionOrientedTransportBindingElement</span></span>

<span data-ttu-id="8a031-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8a031-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a031-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8a031-104">Syntax</span></span>  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8a031-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a031-105">Methods</span></span>  

 <span data-ttu-id="8a031-106">ConnectionOrientedTransportBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="8a031-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8a031-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8a031-107">Properties</span></span>  

 <span data-ttu-id="8a031-108">ConnectionOrientedTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8a031-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="8a031-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="8a031-109">ChannelInitializationTimeout</span></span>  

 <span data-ttu-id="8a031-110">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="8a031-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="8a031-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-112">Zaman aşımından önce kanal başlatmasının ne kadar süreyle tamamlanmasını belirten TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="8a031-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="8a031-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="8a031-113">ConnectionBufferSize</span></span>  

 <span data-ttu-id="8a031-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="8a031-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8a031-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-116">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="8a031-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="8a031-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="8a031-117">HostNameComparisonMode</span></span>  

 <span data-ttu-id="8a031-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8a031-118">Data type: string</span></span>  
  
 <span data-ttu-id="8a031-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-120">URI üzerinde eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="8a031-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="8a031-121">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8a031-121">MaxBufferSize</span></span>  

 <span data-ttu-id="8a031-122">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="8a031-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="8a031-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-124">Kullanılacak arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="8a031-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="8a031-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="8a031-125">MaxOutputDelay</span></span>  

 <span data-ttu-id="8a031-126">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="8a031-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="8a031-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-128">İleti öbeğinin veya bir tam iletinin, gönderilmeden önce bellekte ara belleğe kalabileceği en uzun zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="8a031-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="8a031-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="8a031-129">MaxPendingAccepts</span></span>  

 <span data-ttu-id="8a031-130">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="8a031-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="8a031-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-132">Hizmette gelen bağlantıları işlemek için kullanılabilen, bekleyen zaman uyumsuz kabul iş parçacığı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="8a031-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="8a031-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8a031-133">MaxPendingConnections</span></span>  

 <span data-ttu-id="8a031-134">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="8a031-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="8a031-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-136">Beklemedeki bağlantı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="8a031-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="8a031-137">TransferMode</span><span class="sxs-lookup"><span data-stu-id="8a031-137">TransferMode</span></span>  

 <span data-ttu-id="8a031-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8a031-138">Data type: string</span></span>  
  
 <span data-ttu-id="8a031-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="8a031-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8a031-140">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla birlikte akışa alınıp alınmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8a031-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a031-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a031-141">Requirements</span></span>  
  
|<span data-ttu-id="8a031-142">MOF</span><span class="sxs-lookup"><span data-stu-id="8a031-142">MOF</span></span>|<span data-ttu-id="8a031-143">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8a031-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8a031-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8a031-144">Namespace</span></span>|<span data-ttu-id="8a031-145">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="8a031-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a031-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a031-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
