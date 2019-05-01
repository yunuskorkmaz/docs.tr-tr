---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963312"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="01870-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="01870-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="01870-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="01870-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01870-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01870-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="01870-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="01870-105">Methods</span></span>  
 <span data-ttu-id="01870-106">Hem MsmqTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="01870-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="01870-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="01870-107">Properties</span></span>  
 <span data-ttu-id="01870-108">Hem MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="01870-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="01870-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="01870-109">MaxPoolSize</span></span>  
 <span data-ttu-id="01870-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="01870-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="01870-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01870-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01870-112">İç MSMQ message nesneleri içeren bir havuz en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="01870-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="01870-113">queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="01870-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="01870-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="01870-114">Data type: string</span></span>  
  
 <span data-ttu-id="01870-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01870-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01870-116">Bu bağlamanın kullandığı sıraya konmuş iletişim kanal taşımasını bildiren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="01870-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="01870-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="01870-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="01870-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="01870-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="01870-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01870-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01870-120">Kuyruk adreslerinin Active Directory kullanılarak dönüştürülüp dönüştürülmeyeceğini gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="01870-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01870-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01870-121">Requirements</span></span>  
  
|<span data-ttu-id="01870-122">MOF</span><span class="sxs-lookup"><span data-stu-id="01870-122">MOF</span></span>|<span data-ttu-id="01870-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="01870-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="01870-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="01870-124">Namespace</span></span>|<span data-ttu-id="01870-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="01870-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01870-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01870-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
