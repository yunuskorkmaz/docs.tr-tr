---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: dc7a29e5911a9d0a774e36f5be8c1f3cacad69b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486623"
---
# <a name="transportbindingelement"></a><span data-ttu-id="70daf-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="70daf-102">TransportBindingElement</span></span>
<span data-ttu-id="70daf-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="70daf-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70daf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70daf-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="70daf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="70daf-105">Methods</span></span>  
 <span data-ttu-id="70daf-106">TransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="70daf-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="70daf-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="70daf-107">Properties</span></span>  
 <span data-ttu-id="70daf-108">TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="70daf-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="70daf-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="70daf-109">ManualAddressing</span></span>  
 <span data-ttu-id="70daf-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="70daf-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="70daf-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="70daf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70daf-112">Kullanıcı ileti adresleme denetimini almak istediği olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="70daf-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="70daf-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="70daf-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="70daf-114">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="70daf-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="70daf-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="70daf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70daf-116">Bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="70daf-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="70daf-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="70daf-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="70daf-118">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="70daf-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="70daf-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="70daf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70daf-120">Bu bağlama tarafından işlenen bir ileti için en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="70daf-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="70daf-121">Düzen</span><span class="sxs-lookup"><span data-stu-id="70daf-121">Scheme</span></span>  
 <span data-ttu-id="70daf-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="70daf-122">Data type: string</span></span>  
  
 <span data-ttu-id="70daf-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="70daf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70daf-124">Taşıma için kullanılacak URI düzeni.</span><span class="sxs-lookup"><span data-stu-id="70daf-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70daf-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70daf-125">Requirements</span></span>  
  
|<span data-ttu-id="70daf-126">MOF</span><span class="sxs-lookup"><span data-stu-id="70daf-126">MOF</span></span>|<span data-ttu-id="70daf-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="70daf-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="70daf-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="70daf-128">Namespace</span></span>|<span data-ttu-id="70daf-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="70daf-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70daf-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70daf-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
