---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 303e5523befb68c65bc50ee3933af58897929363
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668463"
---
# <a name="transportbindingelement"></a><span data-ttu-id="99fc3-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="99fc3-102">TransportBindingElement</span></span>
<span data-ttu-id="99fc3-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="99fc3-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fc3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99fc3-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="99fc3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99fc3-105">Methods</span></span>  
 <span data-ttu-id="99fc3-106">TransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="99fc3-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="99fc3-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="99fc3-107">Properties</span></span>  
 <span data-ttu-id="99fc3-108">TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="99fc3-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="99fc3-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="99fc3-109">ManualAddressing</span></span>  
 <span data-ttu-id="99fc3-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="99fc3-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="99fc3-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="99fc3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99fc3-112">Kullanıcının ileti adresleme denetimini ele geçirmesine isteyip istemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="99fc3-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="99fc3-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="99fc3-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="99fc3-114">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="99fc3-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="99fc3-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="99fc3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99fc3-116">Bağlama için en fazla arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="99fc3-117">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="99fc3-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="99fc3-118">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="99fc3-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="99fc3-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="99fc3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99fc3-120">Bu bağlama tarafından işlenen bir ileti için en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="99fc3-121">Düzen</span><span class="sxs-lookup"><span data-stu-id="99fc3-121">Scheme</span></span>  
 <span data-ttu-id="99fc3-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="99fc3-122">Data type: string</span></span>  
  
 <span data-ttu-id="99fc3-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="99fc3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99fc3-124">Taşıma için kullanılacak URI düzeni.</span><span class="sxs-lookup"><span data-stu-id="99fc3-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fc3-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99fc3-125">Requirements</span></span>  
  
|<span data-ttu-id="99fc3-126">MOF</span><span class="sxs-lookup"><span data-stu-id="99fc3-126">MOF</span></span>|<span data-ttu-id="99fc3-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="99fc3-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="99fc3-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="99fc3-128">Namespace</span></span>|<span data-ttu-id="99fc3-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="99fc3-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99fc3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99fc3-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
