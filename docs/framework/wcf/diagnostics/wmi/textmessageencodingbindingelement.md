---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 67c1083daa9acfd204d4de50d4e9178b25aafcf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979023"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="6f8d9-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="6f8d9-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="6f8d9-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="6f8d9-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f8d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f8d9-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6f8d9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6f8d9-105">Methods</span></span>  
 <span data-ttu-id="6f8d9-106">TextMessageEncodingBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="6f8d9-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6f8d9-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6f8d9-107">Properties</span></span>  
 <span data-ttu-id="6f8d9-108">TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6f8d9-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="6f8d9-109">Encoding</span><span class="sxs-lookup"><span data-stu-id="6f8d9-109">Encoding</span></span>  
 <span data-ttu-id="6f8d9-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6f8d9-110">Data type: string</span></span>  
  
 <span data-ttu-id="6f8d9-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6f8d9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f8d9-112">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="6f8d9-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="6f8d9-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="6f8d9-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="6f8d9-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="6f8d9-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6f8d9-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6f8d9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f8d9-116">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f8d9-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="6f8d9-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="6f8d9-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="6f8d9-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="6f8d9-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="6f8d9-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6f8d9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f8d9-120">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="6f8d9-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="6f8d9-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="6f8d9-121">ReaderQuotas</span></span>  
 <span data-ttu-id="6f8d9-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="6f8d9-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="6f8d9-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6f8d9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f8d9-124">Okuyucular kotalar.</span><span class="sxs-lookup"><span data-stu-id="6f8d9-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f8d9-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f8d9-125">Requirements</span></span>  
  
|<span data-ttu-id="6f8d9-126">MOF</span><span class="sxs-lookup"><span data-stu-id="6f8d9-126">MOF</span></span>|<span data-ttu-id="6f8d9-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6f8d9-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6f8d9-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6f8d9-128">Namespace</span></span>|<span data-ttu-id="6f8d9-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6f8d9-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f8d9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f8d9-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
