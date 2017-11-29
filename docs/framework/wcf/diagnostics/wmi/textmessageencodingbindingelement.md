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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6e1eccbaae35a16fe4fb133296698d347c190e94
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="ac8e7-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ac8e7-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="ac8e7-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ac8e7-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac8e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac8e7-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ac8e7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ac8e7-105">Methods</span></span>  
 <span data-ttu-id="ac8e7-106">TextMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ac8e7-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ac8e7-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ac8e7-107">Properties</span></span>  
 <span data-ttu-id="ac8e7-108">TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ac8e7-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="ac8e7-109">Kodlama</span><span class="sxs-lookup"><span data-stu-id="ac8e7-109">Encoding</span></span>  
 <span data-ttu-id="ac8e7-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ac8e7-110">Data type: string</span></span>  
  
 <span data-ttu-id="ac8e7-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac8e7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac8e7-112">Bağlama iletilerde yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="ac8e7-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="ac8e7-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ac8e7-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="ac8e7-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="ac8e7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ac8e7-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac8e7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac8e7-116">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8e7-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="ac8e7-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ac8e7-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="ac8e7-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="ac8e7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="ac8e7-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac8e7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac8e7-120">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac8e7-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="ac8e7-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ac8e7-121">ReaderQuotas</span></span>  
 <span data-ttu-id="ac8e7-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ac8e7-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="ac8e7-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac8e7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac8e7-124">Okuyucu kotaları.</span><span class="sxs-lookup"><span data-stu-id="ac8e7-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac8e7-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac8e7-125">Requirements</span></span>  
  
|<span data-ttu-id="ac8e7-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ac8e7-126">MOF</span></span>|<span data-ttu-id="ac8e7-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ac8e7-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ac8e7-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ac8e7-128">Namespace</span></span>|<span data-ttu-id="ac8e7-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ac8e7-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac8e7-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac8e7-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
