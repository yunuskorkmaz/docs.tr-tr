---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: c5bb7813a680c89eb90f4ccf4ed6f09a831c8095
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262209"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="f6df1-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f6df1-102">XmlDictionaryReaderQuotas</span></span>

<span data-ttu-id="f6df1-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f6df1-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6df1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6df1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f6df1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f6df1-105">Methods</span></span>  

 <span data-ttu-id="f6df1-106">XmlDictionaryReaderQuotas sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f6df1-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f6df1-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f6df1-107">Properties</span></span>  

 <span data-ttu-id="f6df1-108">XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f6df1-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="f6df1-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="f6df1-109">MaxArrayLength</span></span>  

 <span data-ttu-id="f6df1-110">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f6df1-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="f6df1-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f6df1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6df1-112">İzin verilen en büyük dizi uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f6df1-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="f6df1-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="f6df1-113">MaxBytesPerRead</span></span>  

 <span data-ttu-id="f6df1-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f6df1-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f6df1-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f6df1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6df1-116">Her okuma için en fazla izin verilen bayt döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f6df1-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="f6df1-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="f6df1-117">MaxDepth</span></span>  

 <span data-ttu-id="f6df1-118">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f6df1-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f6df1-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f6df1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6df1-120">Her okuma için iç içe geçmiş düğüm derinliği üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="f6df1-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="f6df1-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="f6df1-121">MaxNameTableCharCount</span></span>  

 <span data-ttu-id="f6df1-122">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f6df1-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="f6df1-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f6df1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6df1-124">Tablo adında izin verilen en fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="f6df1-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="f6df1-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="f6df1-125">MaxStringContentLength</span></span>  

 <span data-ttu-id="f6df1-126">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f6df1-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="f6df1-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f6df1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6df1-128">XML öğesi içeriğinde izin verilen en fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="f6df1-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6df1-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6df1-129">Requirements</span></span>  
  
|<span data-ttu-id="f6df1-130">MOF</span><span class="sxs-lookup"><span data-stu-id="f6df1-130">MOF</span></span>|<span data-ttu-id="f6df1-131">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f6df1-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f6df1-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f6df1-132">Namespace</span></span>|<span data-ttu-id="f6df1-133">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="f6df1-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6df1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6df1-134">See also</span></span>

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
