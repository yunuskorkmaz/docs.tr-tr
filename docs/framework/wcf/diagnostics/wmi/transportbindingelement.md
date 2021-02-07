---
description: 'Daha fazla bilgi edinin: TransportBindingElement'
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: de08feaf8abec3a0dfee97e92d68d5223cd0de44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757117"
---
# <a name="transportbindingelement"></a><span data-ttu-id="ab440-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ab440-103">TransportBindingElement</span></span>

<span data-ttu-id="ab440-104">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ab440-104">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab440-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab440-105">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ab440-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ab440-106">Methods</span></span>  

 <span data-ttu-id="ab440-107">TransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ab440-107">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab440-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ab440-108">Properties</span></span>  

 <span data-ttu-id="ab440-109">TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ab440-109">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="ab440-110">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="ab440-110">ManualAddressing</span></span>  

 <span data-ttu-id="ab440-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ab440-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="ab440-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ab440-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab440-113">Kullanıcının ileti adreslemesinin denetimini almak isteyip istemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="ab440-113">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="ab440-114">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="ab440-114">MaxBufferPoolSize</span></span>  

 <span data-ttu-id="ab440-115">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="ab440-115">Data type: sint64</span></span>  
  
 <span data-ttu-id="ab440-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ab440-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab440-117">Bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="ab440-117">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="ab440-118">Değerini</span><span class="sxs-lookup"><span data-stu-id="ab440-118">MaxReceivedMessageSize</span></span>  

 <span data-ttu-id="ab440-119">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="ab440-119">Data type: sint64</span></span>  
  
 <span data-ttu-id="ab440-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ab440-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab440-121">Bu bağlama tarafından işlenen bir ileti için boyut üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="ab440-121">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="ab440-122">Düzen</span><span class="sxs-lookup"><span data-stu-id="ab440-122">Scheme</span></span>  

 <span data-ttu-id="ab440-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ab440-123">Data type: string</span></span>  
  
 <span data-ttu-id="ab440-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ab440-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab440-125">Taşımanın URI şeması.</span><span class="sxs-lookup"><span data-stu-id="ab440-125">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab440-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab440-126">Requirements</span></span>  
  
|<span data-ttu-id="ab440-127">MOF</span><span class="sxs-lookup"><span data-stu-id="ab440-127">MOF</span></span>|<span data-ttu-id="ab440-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab440-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab440-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ab440-129">Namespace</span></span>|<span data-ttu-id="ab440-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="ab440-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab440-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab440-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
