---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50045994"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="d4caa-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d4caa-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="d4caa-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d4caa-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4caa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4caa-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d4caa-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4caa-105">Methods</span></span>  
 <span data-ttu-id="d4caa-106">Hem MsmqTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d4caa-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d4caa-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d4caa-107">Properties</span></span>  
 <span data-ttu-id="d4caa-108">Hem MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d4caa-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="d4caa-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="d4caa-109">MaxPoolSize</span></span>  
 <span data-ttu-id="d4caa-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="d4caa-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="d4caa-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d4caa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4caa-112">İç MSMQ message nesneleri içeren bir havuz en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="d4caa-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="d4caa-113">queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="d4caa-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="d4caa-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d4caa-114">Data type: string</span></span>  
  
 <span data-ttu-id="d4caa-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d4caa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4caa-116">Bu bağlamanın kullandığı sıraya konmuş iletişim kanal taşımasını bildiren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="d4caa-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="d4caa-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="d4caa-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="d4caa-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d4caa-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d4caa-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d4caa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4caa-120">Kuyruk adreslerinin Active Directory kullanılarak dönüştürülüp dönüştürülmeyeceğini gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4caa-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4caa-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4caa-121">Requirements</span></span>  
  
|<span data-ttu-id="d4caa-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d4caa-122">MOF</span></span>|<span data-ttu-id="d4caa-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d4caa-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d4caa-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d4caa-124">Namespace</span></span>|<span data-ttu-id="d4caa-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d4caa-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4caa-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4caa-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
