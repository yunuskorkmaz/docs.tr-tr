---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 04e6abc5941ec99769ff2c15d47881b60e81d2e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181577"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="71183-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="71183-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="71183-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="71183-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71183-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71183-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="71183-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71183-105">Methods</span></span>  
 <span data-ttu-id="71183-106">ConnectionOrientedTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="71183-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="71183-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="71183-107">Properties</span></span>  
 <span data-ttu-id="71183-108">ConnectionOrientedTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="71183-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="71183-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="71183-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="71183-110">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="71183-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="71183-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-112">Zaman aşımından önce tamamlamak ne kadar kanal başlatma belirten bir TimeSpan değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="71183-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="71183-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="71183-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="71183-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="71183-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="71183-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-116">Bir parça istemci veya hizmet serileştirilmiş ileti iletmek için kullanılan arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="71183-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="71183-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="71183-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="71183-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71183-118">Data type: string</span></span>  
  
 <span data-ttu-id="71183-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-120">Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="71183-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="71183-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="71183-121">MaxBufferSize</span></span>  
 <span data-ttu-id="71183-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="71183-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="71183-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-124">Kullanılacak arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="71183-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="71183-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="71183-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="71183-126">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="71183-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="71183-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-128">Gönderilen en fazla bir ileti veya tam bir ileti bir öbek kalabileceği edilmeden önce bellekte arabelleğe zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="71183-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="71183-129">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="71183-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="71183-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="71183-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="71183-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-132">En fazla sayısını bekleyen zaman uyumsuz hizmet gelen bağlantıları işlemek için kullanılan iş parçacıklarının kabul edin.</span><span class="sxs-lookup"><span data-stu-id="71183-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="71183-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="71183-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="71183-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="71183-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="71183-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-136">Bekleyen bağlantılar maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="71183-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="71183-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="71183-137">TransferMode</span></span>  
 <span data-ttu-id="71183-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71183-138">Data type: string</span></span>  
  
 <span data-ttu-id="71183-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71183-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71183-140">İletilerin ara belleğe veya bağlantıya dayalı taşınıp belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="71183-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71183-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71183-141">Requirements</span></span>  
  
|<span data-ttu-id="71183-142">MOF</span><span class="sxs-lookup"><span data-stu-id="71183-142">MOF</span></span>|<span data-ttu-id="71183-143">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="71183-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="71183-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="71183-144">Namespace</span></span>|<span data-ttu-id="71183-145">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="71183-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71183-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71183-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
