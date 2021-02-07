---
description: 'Hakkında daha fazla bilgi edinin: TextMessageEncodingBindingElement'
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 9848f1660642f92c4bce3542fbd404f463b8c84d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757351"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="d8625-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d8625-103">TextMessageEncodingBindingElement</span></span>

<span data-ttu-id="d8625-104">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d8625-104">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8625-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8625-105">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d8625-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d8625-106">Methods</span></span>  

 <span data-ttu-id="d8625-107">TextMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d8625-107">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d8625-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d8625-108">Properties</span></span>  

 <span data-ttu-id="d8625-109">TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d8625-109">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="d8625-110">Encoding</span><span class="sxs-lookup"><span data-stu-id="d8625-110">Encoding</span></span>  

 <span data-ttu-id="d8625-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d8625-111">Data type: string</span></span>  
  
 <span data-ttu-id="d8625-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d8625-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d8625-113">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlaması.</span><span class="sxs-lookup"><span data-stu-id="d8625-113">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="d8625-114">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d8625-114">MaxReadPoolSize</span></span>  

 <span data-ttu-id="d8625-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="d8625-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="d8625-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d8625-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d8625-117">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d8625-117">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="d8625-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d8625-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="d8625-119">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="d8625-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="d8625-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d8625-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d8625-121">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d8625-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="d8625-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d8625-122">ReaderQuotas</span></span>  

 <span data-ttu-id="d8625-123">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d8625-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="d8625-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d8625-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d8625-125">Okuyucuların kotaları.</span><span class="sxs-lookup"><span data-stu-id="d8625-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8625-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8625-126">Requirements</span></span>  
  
|<span data-ttu-id="d8625-127">MOF</span><span class="sxs-lookup"><span data-stu-id="d8625-127">MOF</span></span>|<span data-ttu-id="d8625-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8625-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d8625-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d8625-129">Namespace</span></span>|<span data-ttu-id="d8625-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="d8625-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8625-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8625-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
