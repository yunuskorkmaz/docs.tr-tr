---
description: 'Hakkında daha fazla bilgi edinin: MtomMessageEncodingBindingElement'
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: f06e3d7266c4f7e6f9b4639f7d82941cbabb5dd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803145"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="b80f2-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b80f2-103">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="b80f2-104">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b80f2-104">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b80f2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b80f2-105">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b80f2-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b80f2-106">Methods</span></span>  

 <span data-ttu-id="b80f2-107">MtomMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b80f2-107">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b80f2-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b80f2-108">Properties</span></span>  

 <span data-ttu-id="b80f2-109">MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b80f2-109">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="b80f2-110">Encoding</span><span class="sxs-lookup"><span data-stu-id="b80f2-110">Encoding</span></span>  

 <span data-ttu-id="b80f2-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b80f2-111">Data type: string</span></span>  
  
 <span data-ttu-id="b80f2-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b80f2-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b80f2-113">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlaması.</span><span class="sxs-lookup"><span data-stu-id="b80f2-113">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="b80f2-114">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b80f2-114">MaxReadPoolSize</span></span>  

 <span data-ttu-id="b80f2-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="b80f2-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="b80f2-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b80f2-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b80f2-117">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b80f2-117">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="b80f2-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b80f2-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="b80f2-119">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="b80f2-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="b80f2-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b80f2-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b80f2-121">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b80f2-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="b80f2-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b80f2-122">ReaderQuotas</span></span>  

 <span data-ttu-id="b80f2-123">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b80f2-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="b80f2-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b80f2-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b80f2-125">Okuyucuların kotaları.</span><span class="sxs-lookup"><span data-stu-id="b80f2-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b80f2-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b80f2-126">Requirements</span></span>  
  
|<span data-ttu-id="b80f2-127">MOF</span><span class="sxs-lookup"><span data-stu-id="b80f2-127">MOF</span></span>|<span data-ttu-id="b80f2-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b80f2-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b80f2-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b80f2-129">Namespace</span></span>|<span data-ttu-id="b80f2-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="b80f2-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b80f2-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b80f2-131">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
