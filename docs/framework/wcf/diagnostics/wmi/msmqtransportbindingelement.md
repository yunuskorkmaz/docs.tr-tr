---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 6590c5188e4e1758987a75fbd007099703ea6bc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250430"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="e44af-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e44af-102">MsmqTransportBindingElement</span></span>

<span data-ttu-id="e44af-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e44af-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44af-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e44af-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e44af-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e44af-105">Methods</span></span>  

 <span data-ttu-id="e44af-106">MsmqTransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e44af-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e44af-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e44af-107">Properties</span></span>  

 <span data-ttu-id="e44af-108">MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e44af-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="e44af-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="e44af-109">MaxPoolSize</span></span>  

 <span data-ttu-id="e44af-110">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="e44af-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e44af-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e44af-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e44af-112">İç MSMQ ileti nesneleri içeren havuzun en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="e44af-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="e44af-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="e44af-113">QueueTransferProtocol</span></span>  

 <span data-ttu-id="e44af-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e44af-114">Data type: string</span></span>  
  
 <span data-ttu-id="e44af-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e44af-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e44af-116">Bu bağlamanın kullandığı sıraya alınmış iletişim kanalı aktarımını gösteren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="e44af-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="e44af-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="e44af-117">UseActiveDirectory</span></span>  

 <span data-ttu-id="e44af-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e44af-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e44af-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e44af-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e44af-120">Sıra adreslerinin Active Directory kullanılarak dönüştürülmesi gerekip gerekmediğini belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e44af-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e44af-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e44af-121">Requirements</span></span>  
  
|<span data-ttu-id="e44af-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e44af-122">MOF</span></span>|<span data-ttu-id="e44af-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e44af-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e44af-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e44af-124">Namespace</span></span>|<span data-ttu-id="e44af-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="e44af-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e44af-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e44af-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
