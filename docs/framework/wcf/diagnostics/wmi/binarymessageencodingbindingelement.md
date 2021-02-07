---
description: 'Hakkında daha fazla bilgi edinin: BinaryMessageEncodingBindingElement'
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e2bc711416c61ca29a93fbf75e4e734137f2b4be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757884"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="cce0a-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="cce0a-103">BinaryMessageEncodingBindingElement</span></span>

<span data-ttu-id="cce0a-104">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="cce0a-104">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce0a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cce0a-105">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cce0a-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cce0a-106">Methods</span></span>  

 <span data-ttu-id="cce0a-107">BinaryMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="cce0a-107">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cce0a-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cce0a-108">Properties</span></span>  

 <span data-ttu-id="cce0a-109">BinaryMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cce0a-109">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="cce0a-110">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="cce0a-110">MaxReadPoolSize</span></span>  

 <span data-ttu-id="cce0a-111">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="cce0a-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="cce0a-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="cce0a-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce0a-113">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cce0a-113">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="cce0a-114">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="cce0a-114">MaxSessionSize</span></span>  

 <span data-ttu-id="cce0a-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="cce0a-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="cce0a-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="cce0a-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce0a-117">Kodlama için kullanılan arabelleğin bayt cinsinden boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cce0a-117">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="cce0a-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="cce0a-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="cce0a-119">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="cce0a-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="cce0a-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="cce0a-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce0a-121">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cce0a-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="cce0a-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="cce0a-122">ReaderQuotas</span></span>  

 <span data-ttu-id="cce0a-123">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="cce0a-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="cce0a-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="cce0a-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce0a-125">Okuyucuların kotaları.</span><span class="sxs-lookup"><span data-stu-id="cce0a-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce0a-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cce0a-126">Requirements</span></span>  
  
|<span data-ttu-id="cce0a-127">MOF</span><span class="sxs-lookup"><span data-stu-id="cce0a-127">MOF</span></span>|<span data-ttu-id="cce0a-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cce0a-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cce0a-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cce0a-129">Namespace</span></span>|<span data-ttu-id="cce0a-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="cce0a-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cce0a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cce0a-131">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
