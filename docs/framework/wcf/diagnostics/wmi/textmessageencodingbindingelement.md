---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: f9b94e946413967cc14282e85743a23327683b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486022"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="0e53b-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="0e53b-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="0e53b-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="0e53b-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e53b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e53b-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0e53b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0e53b-105">Methods</span></span>  
 <span data-ttu-id="0e53b-106">TextMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e53b-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0e53b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0e53b-107">Properties</span></span>  
 <span data-ttu-id="0e53b-108">TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0e53b-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="0e53b-109">Kodlama</span><span class="sxs-lookup"><span data-stu-id="0e53b-109">Encoding</span></span>  
 <span data-ttu-id="0e53b-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="0e53b-110">Data type: string</span></span>  
  
 <span data-ttu-id="0e53b-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0e53b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e53b-112">Bağlama iletilerde yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="0e53b-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="0e53b-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="0e53b-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="0e53b-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="0e53b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="0e53b-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0e53b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e53b-116">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e53b-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="0e53b-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="0e53b-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="0e53b-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="0e53b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="0e53b-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0e53b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e53b-120">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e53b-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="0e53b-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="0e53b-121">ReaderQuotas</span></span>  
 <span data-ttu-id="0e53b-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="0e53b-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="0e53b-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0e53b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0e53b-124">Okuyucu kotaları.</span><span class="sxs-lookup"><span data-stu-id="0e53b-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e53b-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e53b-125">Requirements</span></span>  
  
|<span data-ttu-id="0e53b-126">MOF</span><span class="sxs-lookup"><span data-stu-id="0e53b-126">MOF</span></span>|<span data-ttu-id="0e53b-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0e53b-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0e53b-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="0e53b-128">Namespace</span></span>|<span data-ttu-id="0e53b-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0e53b-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e53b-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e53b-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
