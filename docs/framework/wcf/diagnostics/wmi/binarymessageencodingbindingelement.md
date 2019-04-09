---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e0551e7b4b05151490625912742aa6b26ef0216e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145684"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="1c1bf-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1c1bf-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="1c1bf-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1c1bf-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c1bf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c1bf-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1c1bf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1c1bf-105">Methods</span></span>  
 <span data-ttu-id="1c1bf-106">Üst sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1c1bf-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1c1bf-107">Properties</span></span>  
 <span data-ttu-id="1c1bf-108">Üst sınıf aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="1c1bf-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="1c1bf-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="1c1bf-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="1c1bf-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="1c1bf-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c1bf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1bf-112">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="1c1bf-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="1c1bf-113">MaxSessionSize</span></span>  
 <span data-ttu-id="1c1bf-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="1c1bf-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1c1bf-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c1bf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1bf-116">Kodlamak için kullanılan arabelleğin bayt cinsinden boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="1c1bf-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="1c1bf-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="1c1bf-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="1c1bf-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="1c1bf-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c1bf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1bf-120">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="1c1bf-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1c1bf-121">ReaderQuotas</span></span>  
 <span data-ttu-id="1c1bf-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1c1bf-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="1c1bf-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c1bf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1bf-124">Okuyucular kotalar.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c1bf-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c1bf-125">Requirements</span></span>  
  
|<span data-ttu-id="1c1bf-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1c1bf-126">MOF</span></span>|<span data-ttu-id="1c1bf-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1c1bf-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1c1bf-128">Namespace</span></span>|<span data-ttu-id="1c1bf-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c1bf-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c1bf-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c1bf-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
