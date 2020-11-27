---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: eb174d12731d7f1bc78f4d709cf043daf2346bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269801"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="efe64-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="efe64-102">BinaryMessageEncodingBindingElement</span></span>

<span data-ttu-id="efe64-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="efe64-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe64-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="efe64-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="efe64-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="efe64-105">Methods</span></span>  

 <span data-ttu-id="efe64-106">BinaryMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="efe64-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="efe64-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="efe64-107">Properties</span></span>  

 <span data-ttu-id="efe64-108">BinaryMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="efe64-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="efe64-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="efe64-109">MaxReadPoolSize</span></span>  

 <span data-ttu-id="efe64-110">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="efe64-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="efe64-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="efe64-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="efe64-112">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="efe64-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="efe64-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="efe64-113">MaxSessionSize</span></span>  

 <span data-ttu-id="efe64-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="efe64-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="efe64-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="efe64-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="efe64-116">Kodlama için kullanılan arabelleğin bayt cinsinden boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="efe64-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="efe64-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="efe64-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="efe64-118">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="efe64-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="efe64-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="efe64-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="efe64-120">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="efe64-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="efe64-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="efe64-121">ReaderQuotas</span></span>  

 <span data-ttu-id="efe64-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="efe64-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="efe64-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="efe64-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="efe64-124">Okuyucuların kotaları.</span><span class="sxs-lookup"><span data-stu-id="efe64-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe64-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efe64-125">Requirements</span></span>  
  
|<span data-ttu-id="efe64-126">MOF</span><span class="sxs-lookup"><span data-stu-id="efe64-126">MOF</span></span>|<span data-ttu-id="efe64-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="efe64-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="efe64-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="efe64-128">Namespace</span></span>|<span data-ttu-id="efe64-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="efe64-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efe64-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efe64-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
