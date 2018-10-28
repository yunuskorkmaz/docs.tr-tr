---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 79d8b1f4a5127ca36eb57954cff6ee6a97e55e41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182664"
---
# <a name="transportbindingelement"></a><span data-ttu-id="1ec9c-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="1ec9c-102">TransportBindingElement</span></span>
<span data-ttu-id="1ec9c-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="1ec9c-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ec9c-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1ec9c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1ec9c-105">Methods</span></span>  
 <span data-ttu-id="1ec9c-106">TransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1ec9c-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1ec9c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1ec9c-107">Properties</span></span>  
 <span data-ttu-id="1ec9c-108">TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1ec9c-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="1ec9c-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="1ec9c-109">ManualAddressing</span></span>  
 <span data-ttu-id="1ec9c-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1ec9c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1ec9c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1ec9c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ec9c-112">Kullanıcının ileti adresleme denetimini ele geçirmesine isteyip istemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1ec9c-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="1ec9c-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="1ec9c-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="1ec9c-114">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="1ec9c-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="1ec9c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1ec9c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ec9c-116">Bağlama için en fazla arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="1ec9c-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="1ec9c-117">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="1ec9c-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="1ec9c-118">Veri türü: sint64</span><span class="sxs-lookup"><span data-stu-id="1ec9c-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="1ec9c-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1ec9c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ec9c-120">Bu bağlama tarafından işlenen bir ileti için en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="1ec9c-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="1ec9c-121">Düzen</span><span class="sxs-lookup"><span data-stu-id="1ec9c-121">Scheme</span></span>  
 <span data-ttu-id="1ec9c-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1ec9c-122">Data type: string</span></span>  
  
 <span data-ttu-id="1ec9c-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1ec9c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ec9c-124">Taşıma için kullanılacak URI düzeni.</span><span class="sxs-lookup"><span data-stu-id="1ec9c-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ec9c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ec9c-125">Requirements</span></span>  
  
|<span data-ttu-id="1ec9c-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1ec9c-126">MOF</span></span>|<span data-ttu-id="1ec9c-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1ec9c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1ec9c-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1ec9c-128">Namespace</span></span>|<span data-ttu-id="1ec9c-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1ec9c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ec9c-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ec9c-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
