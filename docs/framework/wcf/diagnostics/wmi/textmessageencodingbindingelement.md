---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 966f1ae06f5d7e0dacb8b7d450463c75f783ef1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="e78ea-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e78ea-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="e78ea-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e78ea-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e78ea-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e78ea-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e78ea-105">Methods</span></span>  
 <span data-ttu-id="e78ea-106">TextMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e78ea-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e78ea-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e78ea-107">Properties</span></span>  
 <span data-ttu-id="e78ea-108">TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e78ea-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="e78ea-109">Kodlama</span><span class="sxs-lookup"><span data-stu-id="e78ea-109">Encoding</span></span>  
 <span data-ttu-id="e78ea-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e78ea-110">Data type: string</span></span>  
  
 <span data-ttu-id="e78ea-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e78ea-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e78ea-112">Bağlama iletilerde yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="e78ea-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="e78ea-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e78ea-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="e78ea-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e78ea-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e78ea-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e78ea-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e78ea-116">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78ea-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="e78ea-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e78ea-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="e78ea-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e78ea-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e78ea-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e78ea-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e78ea-120">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="e78ea-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="e78ea-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e78ea-121">ReaderQuotas</span></span>  
 <span data-ttu-id="e78ea-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e78ea-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="e78ea-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e78ea-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e78ea-124">Okuyucu kotaları.</span><span class="sxs-lookup"><span data-stu-id="e78ea-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e78ea-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e78ea-125">Requirements</span></span>  
  
|<span data-ttu-id="e78ea-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e78ea-126">MOF</span></span>|<span data-ttu-id="e78ea-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e78ea-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e78ea-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e78ea-128">Namespace</span></span>|<span data-ttu-id="e78ea-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e78ea-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e78ea-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e78ea-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
