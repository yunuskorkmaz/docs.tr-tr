---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770756"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="a963a-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="a963a-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="a963a-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="a963a-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a963a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a963a-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a963a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a963a-105">Methods</span></span>  
 <span data-ttu-id="a963a-106">Hem MsmqTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a963a-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a963a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a963a-107">Properties</span></span>  
 <span data-ttu-id="a963a-108">Hem MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a963a-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="a963a-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="a963a-109">MaxPoolSize</span></span>  
 <span data-ttu-id="a963a-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="a963a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="a963a-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a963a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a963a-112">İç MSMQ message nesneleri içeren bir havuz en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="a963a-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="a963a-113">queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="a963a-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="a963a-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a963a-114">Data type: string</span></span>  
  
 <span data-ttu-id="a963a-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a963a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a963a-116">Bu bağlamanın kullandığı sıraya konmuş iletişim kanal taşımasını bildiren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="a963a-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="a963a-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="a963a-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="a963a-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="a963a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="a963a-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a963a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a963a-120">Kuyruk adreslerinin Active Directory kullanılarak dönüştürülüp dönüştürülmeyeceğini gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a963a-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a963a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a963a-121">Requirements</span></span>  
  
|<span data-ttu-id="a963a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a963a-122">MOF</span></span>|<span data-ttu-id="a963a-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a963a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a963a-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a963a-124">Namespace</span></span>|<span data-ttu-id="a963a-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a963a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a963a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a963a-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
