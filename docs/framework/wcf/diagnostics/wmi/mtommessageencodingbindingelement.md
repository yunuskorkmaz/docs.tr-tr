---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cc36d7daed1a2cfaf050cbfe9661951117ff66d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="8d998-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8d998-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="8d998-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8d998-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d998-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d998-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8d998-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8d998-105">Methods</span></span>  
 <span data-ttu-id="8d998-106">MtomMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="8d998-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8d998-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8d998-107">Properties</span></span>  
 <span data-ttu-id="8d998-108">MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8d998-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="8d998-109">Kodlama</span><span class="sxs-lookup"><span data-stu-id="8d998-109">Encoding</span></span>  
 <span data-ttu-id="8d998-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8d998-110">Data type: string</span></span>  
  
 <span data-ttu-id="8d998-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8d998-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d998-112">Bağlama iletilerde yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="8d998-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="8d998-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8d998-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="8d998-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8d998-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8d998-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8d998-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d998-116">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d998-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="8d998-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8d998-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="8d998-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8d998-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="8d998-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8d998-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d998-120">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="8d998-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="8d998-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8d998-121">ReaderQuotas</span></span>  
 <span data-ttu-id="8d998-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8d998-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="8d998-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8d998-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d998-124">Okuyucu kotaları.</span><span class="sxs-lookup"><span data-stu-id="8d998-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d998-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d998-125">Requirements</span></span>  
  
|<span data-ttu-id="8d998-126">MOF</span><span class="sxs-lookup"><span data-stu-id="8d998-126">MOF</span></span>|<span data-ttu-id="8d998-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8d998-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8d998-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8d998-128">Namespace</span></span>|<span data-ttu-id="8d998-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8d998-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d998-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d998-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
