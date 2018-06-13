---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 78914d52a9e57fe2e48adcfc0d7b6f911a0d8b3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487834"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="00ffa-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="00ffa-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="00ffa-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="00ffa-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ffa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00ffa-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="00ffa-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="00ffa-105">Methods</span></span>  
 <span data-ttu-id="00ffa-106">XmlDictionaryReaderQuotas sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="00ffa-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="00ffa-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="00ffa-107">Properties</span></span>  
 <span data-ttu-id="00ffa-108">XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="00ffa-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="00ffa-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="00ffa-109">MaxArrayLength</span></span>  
 <span data-ttu-id="00ffa-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="00ffa-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="00ffa-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="00ffa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00ffa-112">Dizi uzunluğu izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="00ffa-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="00ffa-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="00ffa-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="00ffa-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="00ffa-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="00ffa-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="00ffa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00ffa-116">Her okuma için döndürülen bayt izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="00ffa-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="00ffa-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="00ffa-117">MaxDepth</span></span>  
 <span data-ttu-id="00ffa-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="00ffa-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="00ffa-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="00ffa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00ffa-120">Her biri için en fazla iç içe geçen düğüm derinliği okuyun.</span><span class="sxs-lookup"><span data-stu-id="00ffa-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="00ffa-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="00ffa-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="00ffa-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="00ffa-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="00ffa-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="00ffa-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00ffa-124">Bir tablo adı izin verilen maksimum karakter.</span><span class="sxs-lookup"><span data-stu-id="00ffa-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="00ffa-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="00ffa-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="00ffa-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="00ffa-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="00ffa-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="00ffa-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00ffa-128">XML öğesi içeriği izin verilen maksimum karakter.</span><span class="sxs-lookup"><span data-stu-id="00ffa-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ffa-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00ffa-129">Requirements</span></span>  
  
|<span data-ttu-id="00ffa-130">MOF</span><span class="sxs-lookup"><span data-stu-id="00ffa-130">MOF</span></span>|<span data-ttu-id="00ffa-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="00ffa-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="00ffa-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="00ffa-132">Namespace</span></span>|<span data-ttu-id="00ffa-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="00ffa-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00ffa-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00ffa-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
