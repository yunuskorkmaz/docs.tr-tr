---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e0551e7b4b05151490625912742aa6b26ef0216e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768065"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="e614a-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e614a-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="e614a-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e614a-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e614a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e614a-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e614a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e614a-105">Methods</span></span>  
 <span data-ttu-id="e614a-106">Üst sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e614a-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e614a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e614a-107">Properties</span></span>  
 <span data-ttu-id="e614a-108">Üst sınıf aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e614a-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="e614a-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e614a-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="e614a-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e614a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e614a-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e614a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e614a-112">İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e614a-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="e614a-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="e614a-113">MaxSessionSize</span></span>  
 <span data-ttu-id="e614a-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e614a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e614a-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e614a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e614a-116">Kodlamak için kullanılan arabelleğin bayt cinsinden boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e614a-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="e614a-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e614a-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="e614a-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e614a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e614a-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e614a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e614a-120">İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.</span><span class="sxs-lookup"><span data-stu-id="e614a-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="e614a-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e614a-121">ReaderQuotas</span></span>  
 <span data-ttu-id="e614a-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e614a-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="e614a-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e614a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e614a-124">Okuyucular kotalar.</span><span class="sxs-lookup"><span data-stu-id="e614a-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e614a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e614a-125">Requirements</span></span>  
  
|<span data-ttu-id="e614a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e614a-126">MOF</span></span>|<span data-ttu-id="e614a-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e614a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e614a-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e614a-128">Namespace</span></span>|<span data-ttu-id="e614a-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e614a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e614a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e614a-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
