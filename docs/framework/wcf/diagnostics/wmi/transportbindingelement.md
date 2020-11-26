---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 45bfcd069391156bc85cc4c26f2b172770197a9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234849"
---
# <a name="transportbindingelement"></a><span data-ttu-id="01bf9-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="01bf9-102">TransportBindingElement</span></span>

<span data-ttu-id="01bf9-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="01bf9-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01bf9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="01bf9-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="01bf9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="01bf9-105">Methods</span></span>  

 <span data-ttu-id="01bf9-106">TransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="01bf9-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="01bf9-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="01bf9-107">Properties</span></span>  

 <span data-ttu-id="01bf9-108">TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="01bf9-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="01bf9-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="01bf9-109">ManualAddressing</span></span>  

 <span data-ttu-id="01bf9-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="01bf9-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="01bf9-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="01bf9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01bf9-112">Kullanıcının ileti adreslemesinin denetimini almak isteyip istemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="01bf9-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="01bf9-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="01bf9-113">MaxBufferPoolSize</span></span>  

 <span data-ttu-id="01bf9-114">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="01bf9-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="01bf9-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="01bf9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01bf9-116">Bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="01bf9-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="01bf9-117">Değerini</span><span class="sxs-lookup"><span data-stu-id="01bf9-117">MaxReceivedMessageSize</span></span>  

 <span data-ttu-id="01bf9-118">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="01bf9-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="01bf9-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="01bf9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01bf9-120">Bu bağlama tarafından işlenen bir ileti için boyut üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="01bf9-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="01bf9-121">Düzen</span><span class="sxs-lookup"><span data-stu-id="01bf9-121">Scheme</span></span>  

 <span data-ttu-id="01bf9-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="01bf9-122">Data type: string</span></span>  
  
 <span data-ttu-id="01bf9-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="01bf9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01bf9-124">Taşımanın URI şeması.</span><span class="sxs-lookup"><span data-stu-id="01bf9-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01bf9-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01bf9-125">Requirements</span></span>  
  
|<span data-ttu-id="01bf9-126">MOF</span><span class="sxs-lookup"><span data-stu-id="01bf9-126">MOF</span></span>|<span data-ttu-id="01bf9-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01bf9-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="01bf9-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="01bf9-128">Namespace</span></span>|<span data-ttu-id="01bf9-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="01bf9-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01bf9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01bf9-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
