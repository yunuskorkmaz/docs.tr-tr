---
description: 'Hakkında daha fazla bilgi edinin: ConnectionOrientedTransportBindingElement'
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: bd0c05fc86ad7bc95837cee7e22ea83975369b62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757585"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="bc0d8-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bc0d8-103">ConnectionOrientedTransportBindingElement</span></span>

<span data-ttu-id="bc0d8-104">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bc0d8-104">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0d8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc0d8-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="bc0d8-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bc0d8-106">Methods</span></span>  

 <span data-ttu-id="bc0d8-107">ConnectionOrientedTransportBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-107">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bc0d8-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bc0d8-108">Properties</span></span>  

 <span data-ttu-id="bc0d8-109">ConnectionOrientedTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bc0d8-109">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="bc0d8-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="bc0d8-110">ChannelInitializationTimeout</span></span>  

 <span data-ttu-id="bc0d8-111">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="bc0d8-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="bc0d8-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-113">Zaman aşımından önce kanal başlatmasının ne kadar süreyle tamamlanmasını belirten TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-113">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="bc0d8-114">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="bc0d8-114">ConnectionBufferSize</span></span>  

 <span data-ttu-id="bc0d8-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="bc0d8-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="bc0d8-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-117">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-117">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="bc0d8-118">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bc0d8-118">HostNameComparisonMode</span></span>  

 <span data-ttu-id="bc0d8-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bc0d8-119">Data type: string</span></span>  
  
 <span data-ttu-id="bc0d8-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-121">URI üzerinde eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-121">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="bc0d8-122">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="bc0d8-122">MaxBufferSize</span></span>  

 <span data-ttu-id="bc0d8-123">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="bc0d8-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="bc0d8-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-125">Kullanılacak arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-125">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="bc0d8-126">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="bc0d8-126">MaxOutputDelay</span></span>  

 <span data-ttu-id="bc0d8-127">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="bc0d8-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="bc0d8-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-129">İleti öbeğinin veya bir tam iletinin, gönderilmeden önce bellekte ara belleğe kalabileceği en uzun zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-129">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="bc0d8-130">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="bc0d8-130">MaxPendingAccepts</span></span>  

 <span data-ttu-id="bc0d8-131">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="bc0d8-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="bc0d8-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-133">Hizmette gelen bağlantıları işlemek için kullanılabilen, bekleyen zaman uyumsuz kabul iş parçacığı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-133">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="bc0d8-134">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="bc0d8-134">MaxPendingConnections</span></span>  

 <span data-ttu-id="bc0d8-135">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="bc0d8-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="bc0d8-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-137">Beklemedeki bağlantı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-137">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="bc0d8-138">TransferMode</span><span class="sxs-lookup"><span data-stu-id="bc0d8-138">TransferMode</span></span>  

 <span data-ttu-id="bc0d8-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bc0d8-139">Data type: string</span></span>  
  
 <span data-ttu-id="bc0d8-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="bc0d8-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc0d8-141">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla birlikte akışa alınıp alınmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-141">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0d8-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc0d8-142">Requirements</span></span>  
  
|<span data-ttu-id="bc0d8-143">MOF</span><span class="sxs-lookup"><span data-stu-id="bc0d8-143">MOF</span></span>|<span data-ttu-id="bc0d8-144">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bc0d8-145">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="bc0d8-145">Namespace</span></span>|<span data-ttu-id="bc0d8-146">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="bc0d8-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc0d8-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc0d8-147">See also</span></span>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
