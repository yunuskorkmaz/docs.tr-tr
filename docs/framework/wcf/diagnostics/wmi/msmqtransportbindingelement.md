---
description: 'Daha fazla bilgi edinin: MsmqTransportBindingElement'
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 4b6f363d979972c6ff0a2a378906feeece2ff6b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803158"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="4b24b-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4b24b-103">MsmqTransportBindingElement</span></span>

<span data-ttu-id="4b24b-104">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4b24b-104">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b24b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b24b-105">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4b24b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4b24b-106">Methods</span></span>  

 <span data-ttu-id="4b24b-107">MsmqTransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4b24b-107">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4b24b-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4b24b-108">Properties</span></span>  

 <span data-ttu-id="4b24b-109">MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4b24b-109">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="4b24b-110">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="4b24b-110">MaxPoolSize</span></span>  

 <span data-ttu-id="4b24b-111">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="4b24b-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="4b24b-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4b24b-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4b24b-113">İç MSMQ ileti nesneleri içeren havuzun en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="4b24b-113">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="4b24b-114">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="4b24b-114">QueueTransferProtocol</span></span>  

 <span data-ttu-id="4b24b-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="4b24b-115">Data type: string</span></span>  
  
 <span data-ttu-id="4b24b-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4b24b-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4b24b-117">Bu bağlamanın kullandığı sıraya alınmış iletişim kanalı aktarımını gösteren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="4b24b-117">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="4b24b-118">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="4b24b-118">UseActiveDirectory</span></span>  

 <span data-ttu-id="4b24b-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="4b24b-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="4b24b-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4b24b-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4b24b-121">Sıra adreslerinin Active Directory kullanılarak dönüştürülmesi gerekip gerekmediğini belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b24b-121">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b24b-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b24b-122">Requirements</span></span>  
  
|<span data-ttu-id="4b24b-123">MOF</span><span class="sxs-lookup"><span data-stu-id="4b24b-123">MOF</span></span>|<span data-ttu-id="4b24b-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4b24b-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4b24b-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4b24b-125">Namespace</span></span>|<span data-ttu-id="4b24b-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="4b24b-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b24b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b24b-127">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
