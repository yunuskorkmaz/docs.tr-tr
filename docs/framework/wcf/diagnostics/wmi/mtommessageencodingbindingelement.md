---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: b4d8503543c93d0112fc39e4b2dba5434bc56472
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237410"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="38b84-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="38b84-102">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="38b84-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="38b84-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b84-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="38b84-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="38b84-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38b84-105">Methods</span></span>  

 <span data-ttu-id="38b84-106">MtomMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="38b84-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="38b84-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="38b84-107">Properties</span></span>  

 <span data-ttu-id="38b84-108">MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="38b84-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="38b84-109">Encoding</span><span class="sxs-lookup"><span data-stu-id="38b84-109">Encoding</span></span>  

 <span data-ttu-id="38b84-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="38b84-110">Data type: string</span></span>  
  
 <span data-ttu-id="38b84-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38b84-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b84-112">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlaması.</span><span class="sxs-lookup"><span data-stu-id="38b84-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="38b84-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="38b84-113">MaxReadPoolSize</span></span>  

 <span data-ttu-id="38b84-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="38b84-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="38b84-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38b84-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b84-116">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="38b84-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="38b84-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="38b84-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="38b84-118">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="38b84-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="38b84-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38b84-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b84-120">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="38b84-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="38b84-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="38b84-121">ReaderQuotas</span></span>  

 <span data-ttu-id="38b84-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="38b84-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="38b84-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38b84-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b84-124">Okuyucuların kotaları.</span><span class="sxs-lookup"><span data-stu-id="38b84-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38b84-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38b84-125">Requirements</span></span>  
  
|<span data-ttu-id="38b84-126">MOF</span><span class="sxs-lookup"><span data-stu-id="38b84-126">MOF</span></span>|<span data-ttu-id="38b84-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38b84-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="38b84-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="38b84-128">Namespace</span></span>|<span data-ttu-id="38b84-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="38b84-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38b84-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38b84-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
