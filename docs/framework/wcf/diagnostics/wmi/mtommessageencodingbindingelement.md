---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 49a640a666131491366646d6d486d25a515e35bf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185712"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="bd88b-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd88b-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="bd88b-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd88b-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd88b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd88b-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bd88b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bd88b-105">Methods</span></span>  
 <span data-ttu-id="bd88b-106">MtomMessageEncodingBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="bd88b-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bd88b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bd88b-107">Properties</span></span>  
 <span data-ttu-id="bd88b-108">MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bd88b-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="bd88b-109">Kodlama</span><span class="sxs-lookup"><span data-stu-id="bd88b-109">Encoding</span></span>  
 <span data-ttu-id="bd88b-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bd88b-110">Data type: string</span></span>  
  
 <span data-ttu-id="bd88b-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bd88b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd88b-112">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="bd88b-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="bd88b-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="bd88b-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="bd88b-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="bd88b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="bd88b-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bd88b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd88b-116">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd88b-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="bd88b-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="bd88b-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="bd88b-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="bd88b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="bd88b-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bd88b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd88b-120">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="bd88b-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="bd88b-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="bd88b-121">ReaderQuotas</span></span>  
 <span data-ttu-id="bd88b-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="bd88b-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="bd88b-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bd88b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd88b-124">Okuyucular kotalar.</span><span class="sxs-lookup"><span data-stu-id="bd88b-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd88b-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd88b-125">Requirements</span></span>  
  
|<span data-ttu-id="bd88b-126">MOF</span><span class="sxs-lookup"><span data-stu-id="bd88b-126">MOF</span></span>|<span data-ttu-id="bd88b-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bd88b-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bd88b-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="bd88b-128">Namespace</span></span>|<span data-ttu-id="bd88b-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bd88b-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd88b-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd88b-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
