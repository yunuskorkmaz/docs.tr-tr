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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09d43ed76ef70f4478aa1029c254a7b1686a8d08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="cf9fa-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="cf9fa-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="cf9fa-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="cf9fa-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf9fa-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cf9fa-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cf9fa-105">Methods</span></span>  
 <span data-ttu-id="cf9fa-106">BinaryMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cf9fa-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cf9fa-107">Properties</span></span>  
 <span data-ttu-id="cf9fa-108">BinaryMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="cf9fa-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="cf9fa-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="cf9fa-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cf9fa-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="cf9fa-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf9fa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf9fa-112">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="cf9fa-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="cf9fa-113">MaxSessionSize</span></span>  
 <span data-ttu-id="cf9fa-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cf9fa-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="cf9fa-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf9fa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf9fa-116">Kodlama için kullanılan arabelleğin bayt cinsinden boyutu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="cf9fa-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="cf9fa-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="cf9fa-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cf9fa-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="cf9fa-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf9fa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf9fa-120">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="cf9fa-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="cf9fa-121">ReaderQuotas</span></span>  
 <span data-ttu-id="cf9fa-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="cf9fa-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="cf9fa-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf9fa-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf9fa-124">Okuyucu kotaları.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf9fa-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf9fa-125">Requirements</span></span>  
  
|<span data-ttu-id="cf9fa-126">MOF</span><span class="sxs-lookup"><span data-stu-id="cf9fa-126">MOF</span></span>|<span data-ttu-id="cf9fa-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cf9fa-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cf9fa-128">Namespace</span></span>|<span data-ttu-id="cf9fa-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cf9fa-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf9fa-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf9fa-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
