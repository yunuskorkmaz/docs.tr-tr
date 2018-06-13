---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 03a33f01fe6b6f75e81749c96c31770009350b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486569"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="2f578-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2f578-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="2f578-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2f578-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f578-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f578-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2f578-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2f578-105">Methods</span></span>  
 <span data-ttu-id="2f578-106">BinaryMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="2f578-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2f578-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2f578-107">Properties</span></span>  
 <span data-ttu-id="2f578-108">BinaryMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2f578-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="2f578-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="2f578-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="2f578-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2f578-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="2f578-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2f578-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2f578-112">Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f578-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="2f578-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="2f578-113">MaxSessionSize</span></span>  
 <span data-ttu-id="2f578-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2f578-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2f578-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2f578-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2f578-116">Kodlama için kullanılan arabelleğin bayt cinsinden boyutu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2f578-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="2f578-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="2f578-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="2f578-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2f578-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="2f578-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2f578-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2f578-120">Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="2f578-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="2f578-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2f578-121">ReaderQuotas</span></span>  
 <span data-ttu-id="2f578-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2f578-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="2f578-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2f578-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2f578-124">Okuyucu kotaları.</span><span class="sxs-lookup"><span data-stu-id="2f578-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f578-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f578-125">Requirements</span></span>  
  
|<span data-ttu-id="2f578-126">MOF</span><span class="sxs-lookup"><span data-stu-id="2f578-126">MOF</span></span>|<span data-ttu-id="2f578-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2f578-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2f578-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2f578-128">Namespace</span></span>|<span data-ttu-id="2f578-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2f578-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f578-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f578-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
