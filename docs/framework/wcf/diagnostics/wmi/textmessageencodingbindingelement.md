---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 2371c38aebe2bd8d6da93d702801556fad986ef9
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452579"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="a2300-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="a2300-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="a2300-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="a2300-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2300-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2300-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a2300-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a2300-105">Methods</span></span>  
 <span data-ttu-id="a2300-106">TextMessageEncodingBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a2300-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a2300-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a2300-107">Properties</span></span>  
 <span data-ttu-id="a2300-108">TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a2300-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="a2300-109">Kodlama</span><span class="sxs-lookup"><span data-stu-id="a2300-109">Encoding</span></span>  
 <span data-ttu-id="a2300-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a2300-110">Data type: string</span></span>  
  
 <span data-ttu-id="a2300-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2300-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2300-112">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="a2300-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="a2300-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a2300-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="a2300-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="a2300-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="a2300-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2300-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2300-116">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2300-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="a2300-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a2300-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="a2300-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="a2300-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="a2300-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2300-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2300-120">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="a2300-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="a2300-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="a2300-121">ReaderQuotas</span></span>  
 <span data-ttu-id="a2300-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="a2300-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="a2300-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2300-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2300-124">Okuyucular kotalar.</span><span class="sxs-lookup"><span data-stu-id="a2300-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2300-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2300-125">Requirements</span></span>  
  
|<span data-ttu-id="a2300-126">MOF</span><span class="sxs-lookup"><span data-stu-id="a2300-126">MOF</span></span>|<span data-ttu-id="a2300-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a2300-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a2300-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a2300-128">Namespace</span></span>|<span data-ttu-id="a2300-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a2300-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2300-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2300-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
