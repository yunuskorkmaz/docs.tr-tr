---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c0ff11752ae1030e574182cfb825fb87ddc8c7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="59ab2-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="59ab2-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="59ab2-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="59ab2-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ab2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59ab2-104">Syntax</span></span>  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="59ab2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59ab2-105">Methods</span></span>  
 <span data-ttu-id="59ab2-106">XmlDictionaryReaderQuotas sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="59ab2-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="59ab2-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="59ab2-107">Properties</span></span>  
 <span data-ttu-id="59ab2-108">XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="59ab2-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="59ab2-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="59ab2-109">MaxArrayLength</span></span>  
 <span data-ttu-id="59ab2-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="59ab2-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="59ab2-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59ab2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59ab2-112">Dizi uzunluğu izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="59ab2-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="59ab2-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="59ab2-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="59ab2-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="59ab2-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="59ab2-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59ab2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59ab2-116">Her okuma için döndürülen bayt izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="59ab2-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="59ab2-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="59ab2-117">MaxDepth</span></span>  
 <span data-ttu-id="59ab2-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="59ab2-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="59ab2-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59ab2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59ab2-120">Her biri için en fazla iç içe geçen düğüm derinliği okuyun.</span><span class="sxs-lookup"><span data-stu-id="59ab2-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="59ab2-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="59ab2-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="59ab2-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="59ab2-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="59ab2-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59ab2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59ab2-124">Bir tablo adı izin verilen maksimum karakter.</span><span class="sxs-lookup"><span data-stu-id="59ab2-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="59ab2-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="59ab2-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="59ab2-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="59ab2-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="59ab2-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59ab2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59ab2-128">XML öğesi içeriği izin verilen maksimum karakter.</span><span class="sxs-lookup"><span data-stu-id="59ab2-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ab2-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59ab2-129">Requirements</span></span>  
  
|<span data-ttu-id="59ab2-130">MOF</span><span class="sxs-lookup"><span data-stu-id="59ab2-130">MOF</span></span>|<span data-ttu-id="59ab2-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="59ab2-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="59ab2-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="59ab2-132">Namespace</span></span>|<span data-ttu-id="59ab2-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="59ab2-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59ab2-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59ab2-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
