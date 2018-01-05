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
ms.workload: dotnet
ms.openlocfilehash: 1a3afb9b8cfede60c773d146f4d1728d7fe02b75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="2c218-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2c218-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="2c218-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2c218-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c218-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c218-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="2c218-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2c218-105">Methods</span></span>  
 <span data-ttu-id="2c218-106">XmlDictionaryReaderQuotas sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="2c218-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2c218-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2c218-107">Properties</span></span>  
 <span data-ttu-id="2c218-108">XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2c218-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="2c218-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="2c218-109">MaxArrayLength</span></span>  
 <span data-ttu-id="2c218-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2c218-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="2c218-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2c218-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2c218-112">Dizi uzunluğu izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="2c218-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="2c218-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="2c218-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="2c218-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2c218-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2c218-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2c218-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2c218-116">Her okuma için döndürülen bayt izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="2c218-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="2c218-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="2c218-117">MaxDepth</span></span>  
 <span data-ttu-id="2c218-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2c218-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="2c218-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2c218-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2c218-120">Her biri için en fazla iç içe geçen düğüm derinliği okuyun.</span><span class="sxs-lookup"><span data-stu-id="2c218-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="2c218-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="2c218-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="2c218-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2c218-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="2c218-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2c218-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2c218-124">Bir tablo adı izin verilen maksimum karakter.</span><span class="sxs-lookup"><span data-stu-id="2c218-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="2c218-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="2c218-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="2c218-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2c218-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="2c218-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2c218-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2c218-128">XML öğesi içeriği izin verilen maksimum karakter.</span><span class="sxs-lookup"><span data-stu-id="2c218-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c218-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c218-129">Requirements</span></span>  
  
|<span data-ttu-id="2c218-130">MOF</span><span class="sxs-lookup"><span data-stu-id="2c218-130">MOF</span></span>|<span data-ttu-id="2c218-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2c218-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2c218-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2c218-132">Namespace</span></span>|<span data-ttu-id="2c218-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2c218-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c218-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c218-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
