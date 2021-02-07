---
description: 'Daha fazla bilgi edinin: XmlDictionaryReaderQuotas'
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: d1450051e7107e9b92f848d26e6b182bfd2f2340
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756870"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="41b7c-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="41b7c-103">XmlDictionaryReaderQuotas</span></span>

<span data-ttu-id="41b7c-104">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="41b7c-104">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b7c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="41b7c-105">Syntax</span></span>  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="41b7c-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="41b7c-106">Methods</span></span>  

 <span data-ttu-id="41b7c-107">XmlDictionaryReaderQuotas sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="41b7c-107">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="41b7c-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="41b7c-108">Properties</span></span>  

 <span data-ttu-id="41b7c-109">XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="41b7c-109">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="41b7c-110">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="41b7c-110">MaxArrayLength</span></span>  

 <span data-ttu-id="41b7c-111">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="41b7c-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="41b7c-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="41b7c-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41b7c-113">İzin verilen en büyük dizi uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="41b7c-113">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="41b7c-114">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="41b7c-114">MaxBytesPerRead</span></span>  

 <span data-ttu-id="41b7c-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="41b7c-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="41b7c-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="41b7c-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41b7c-117">Her okuma için en fazla izin verilen bayt döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="41b7c-117">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="41b7c-118">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="41b7c-118">MaxDepth</span></span>  

 <span data-ttu-id="41b7c-119">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="41b7c-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="41b7c-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="41b7c-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41b7c-121">Her okuma için iç içe geçmiş düğüm derinliği üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="41b7c-121">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="41b7c-122">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="41b7c-122">MaxNameTableCharCount</span></span>  

 <span data-ttu-id="41b7c-123">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="41b7c-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="41b7c-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="41b7c-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41b7c-125">Tablo adında izin verilen en fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="41b7c-125">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="41b7c-126">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="41b7c-126">MaxStringContentLength</span></span>  

 <span data-ttu-id="41b7c-127">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="41b7c-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="41b7c-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="41b7c-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41b7c-129">XML öğesi içeriğinde izin verilen en fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="41b7c-129">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b7c-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41b7c-130">Requirements</span></span>  
  
|<span data-ttu-id="41b7c-131">MOF</span><span class="sxs-lookup"><span data-stu-id="41b7c-131">MOF</span></span>|<span data-ttu-id="41b7c-132">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41b7c-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="41b7c-133">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="41b7c-133">Namespace</span></span>|<span data-ttu-id="41b7c-134">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="41b7c-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41b7c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41b7c-135">See also</span></span>

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
