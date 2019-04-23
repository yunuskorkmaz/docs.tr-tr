---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978178"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="62478-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="62478-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="62478-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="62478-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62478-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62478-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="62478-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="62478-105">Methods</span></span>  
 <span data-ttu-id="62478-106">MtomMessageEncodingBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="62478-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="62478-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="62478-107">Properties</span></span>  
 <span data-ttu-id="62478-108">MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="62478-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="62478-109">Encoding</span><span class="sxs-lookup"><span data-stu-id="62478-109">Encoding</span></span>  
 <span data-ttu-id="62478-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="62478-110">Data type: string</span></span>  
  
 <span data-ttu-id="62478-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62478-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62478-112">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="62478-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="62478-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="62478-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="62478-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="62478-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="62478-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62478-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62478-116">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62478-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="62478-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="62478-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="62478-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="62478-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="62478-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62478-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62478-120">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="62478-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="62478-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="62478-121">ReaderQuotas</span></span>  
 <span data-ttu-id="62478-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="62478-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="62478-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62478-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62478-124">Okuyucular kotalar.</span><span class="sxs-lookup"><span data-stu-id="62478-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62478-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62478-125">Requirements</span></span>  
  
|<span data-ttu-id="62478-126">MOF</span><span class="sxs-lookup"><span data-stu-id="62478-126">MOF</span></span>|<span data-ttu-id="62478-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="62478-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="62478-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="62478-128">Namespace</span></span>|<span data-ttu-id="62478-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="62478-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62478-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62478-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
