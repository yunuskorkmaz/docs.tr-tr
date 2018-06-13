---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485914"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="92af7-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="92af7-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="92af7-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="92af7-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92af7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92af7-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="92af7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="92af7-105">Methods</span></span>  
 <span data-ttu-id="92af7-106">Hem MsmqTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="92af7-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="92af7-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="92af7-107">Properties</span></span>  
 <span data-ttu-id="92af7-108">Hem MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="92af7-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="92af7-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="92af7-109">MaxPoolSize</span></span>  
 <span data-ttu-id="92af7-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="92af7-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="92af7-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="92af7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92af7-112">İç MSMQ İleti nesneleri içeren havuzu en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="92af7-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="92af7-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="92af7-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="92af7-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="92af7-114">Data type: string</span></span>  
  
 <span data-ttu-id="92af7-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="92af7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92af7-116">Bu bağlamayı kullanan kuyruğa alınan iletişim kanalı aktarım gösteren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="92af7-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="92af7-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="92af7-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="92af7-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="92af7-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="92af7-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="92af7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92af7-120">Active Directory'yi kullanarak sıra adreslerini dönüştürülüp dönüştürülmeyeceğini gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="92af7-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92af7-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92af7-121">Requirements</span></span>  
  
|<span data-ttu-id="92af7-122">MOF</span><span class="sxs-lookup"><span data-stu-id="92af7-122">MOF</span></span>|<span data-ttu-id="92af7-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="92af7-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="92af7-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="92af7-124">Namespace</span></span>|<span data-ttu-id="92af7-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="92af7-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92af7-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92af7-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
