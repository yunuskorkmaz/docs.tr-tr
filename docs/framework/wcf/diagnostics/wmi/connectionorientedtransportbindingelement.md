---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 3b1055e6e2329fd213ae973ad32cdf8014d30a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487454"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="e417f-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e417f-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="e417f-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e417f-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e417f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e417f-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="e417f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e417f-105">Methods</span></span>  
 <span data-ttu-id="e417f-106">ConnectionOrientedTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e417f-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e417f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e417f-107">Properties</span></span>  
 <span data-ttu-id="e417f-108">ConnectionOrientedTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e417f-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="e417f-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="e417f-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="e417f-110">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e417f-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="e417f-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-112">Zaman aşımından önce tamamlamak ne kadar süreyle kanal başlatma belirten timespan sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e417f-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="e417f-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="e417f-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="e417f-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e417f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e417f-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-116">İstemci veya hizmet hattan serileştirilmiş iletide öbeğini iletmek için kullanılan arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e417f-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="e417f-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="e417f-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="e417f-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e417f-118">Data type: string</span></span>  
  
 <span data-ttu-id="e417f-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-120">Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="e417f-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="e417f-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="e417f-121">MaxBufferSize</span></span>  
 <span data-ttu-id="e417f-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e417f-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e417f-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-124">Kullanılacak arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="e417f-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="e417f-125">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="e417f-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="e417f-126">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e417f-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="e417f-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-128">En fazla bellek önce arabelleğe bir ileti veya tam bir ileti öbeğini kalabileceği zaman aralığını gönderilen.</span><span class="sxs-lookup"><span data-stu-id="e417f-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="e417f-129">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="e417f-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="e417f-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e417f-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="e417f-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-132">En fazla bekleyen zaman uyumsuz hizmet gelen bağlantıları işlemek için kullanılan iş parçacıklarını kabul edin.</span><span class="sxs-lookup"><span data-stu-id="e417f-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="e417f-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e417f-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="e417f-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e417f-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e417f-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-136">Beklemedeki bağlantı maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e417f-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="e417f-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="e417f-137">TransferMode</span></span>  
 <span data-ttu-id="e417f-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e417f-138">Data type: string</span></span>  
  
 <span data-ttu-id="e417f-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e417f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e417f-140">İletilerin ara belleğe veya ile bağlantı yönelimli aktarma akışı olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e417f-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e417f-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e417f-141">Requirements</span></span>  
  
|<span data-ttu-id="e417f-142">MOF</span><span class="sxs-lookup"><span data-stu-id="e417f-142">MOF</span></span>|<span data-ttu-id="e417f-143">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e417f-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e417f-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e417f-144">Namespace</span></span>|<span data-ttu-id="e417f-145">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e417f-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e417f-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e417f-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
