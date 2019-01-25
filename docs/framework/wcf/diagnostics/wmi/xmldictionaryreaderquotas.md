---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f24865fb0affa7b4516a14fc05b905995826e82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597677"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="9b981-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9b981-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="9b981-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9b981-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b981-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b981-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9b981-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9b981-105">Methods</span></span>  
 <span data-ttu-id="9b981-106">XmlDictionaryReaderQuotas sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9b981-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9b981-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9b981-107">Properties</span></span>  
 <span data-ttu-id="9b981-108">XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9b981-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="9b981-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="9b981-109">MaxArrayLength</span></span>  
 <span data-ttu-id="9b981-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9b981-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b981-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9b981-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b981-112">Dizi uzunluğu izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="9b981-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="9b981-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="9b981-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="9b981-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9b981-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b981-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9b981-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b981-116">Her okuma için döndürülen bayt sayısı izin verilen en fazla.</span><span class="sxs-lookup"><span data-stu-id="9b981-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="9b981-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="9b981-117">MaxDepth</span></span>  
 <span data-ttu-id="9b981-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9b981-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b981-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9b981-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b981-120">Her biri için en fazla iç içe geçen düğüm derinliği okuyun.</span><span class="sxs-lookup"><span data-stu-id="9b981-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="9b981-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="9b981-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="9b981-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9b981-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b981-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9b981-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b981-124">Tablo adınında izin verilen en fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="9b981-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="9b981-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="9b981-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="9b981-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9b981-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="9b981-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9b981-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b981-128">XML öğesi içeriğinde izin verilen en fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="9b981-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b981-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b981-129">Requirements</span></span>  
  
|<span data-ttu-id="9b981-130">MOF</span><span class="sxs-lookup"><span data-stu-id="9b981-130">MOF</span></span>|<span data-ttu-id="9b981-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9b981-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9b981-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9b981-132">Namespace</span></span>|<span data-ttu-id="9b981-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9b981-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b981-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b981-134">See also</span></span>
- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
