---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="496f8-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="496f8-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="496f8-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="496f8-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="496f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="496f8-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="496f8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="496f8-105">Methods</span></span>  
 <span data-ttu-id="496f8-106">BinaryMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="496f8-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="496f8-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="496f8-107">Properties</span></span>  
 <span data-ttu-id="496f8-108">BinaryMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="496f8-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="496f8-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="496f8-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="496f8-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="496f8-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="496f8-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="496f8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="496f8-112">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="496f8-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="496f8-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="496f8-113">MaxSessionSize</span></span>  
 <span data-ttu-id="496f8-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="496f8-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="496f8-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="496f8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="496f8-116">Kodlama için kullanılan arabelleğin bayt cinsinden boyutu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="496f8-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="496f8-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="496f8-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="496f8-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="496f8-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="496f8-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="496f8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="496f8-120">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="496f8-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="496f8-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="496f8-121">ReaderQuotas</span></span>  
 <span data-ttu-id="496f8-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="496f8-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="496f8-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="496f8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="496f8-124">Okuyucu kotaları.</span><span class="sxs-lookup"><span data-stu-id="496f8-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="496f8-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="496f8-125">Requirements</span></span>  
  
|<span data-ttu-id="496f8-126">MOF</span><span class="sxs-lookup"><span data-stu-id="496f8-126">MOF</span></span>|<span data-ttu-id="496f8-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="496f8-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="496f8-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="496f8-128">Namespace</span></span>|<span data-ttu-id="496f8-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="496f8-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="496f8-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="496f8-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
