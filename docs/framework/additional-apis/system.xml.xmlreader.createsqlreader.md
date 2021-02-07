---
description: 'Şu konuda daha fazla bilgi edinin: XmlReader. CreateSqlReader yöntemi'
title: XmlReader. CreateSqlReader yöntemi (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 61d594c0438c86863ce4052387439f5483d8a34c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740443"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="b86ea-103">XmlReader.CreateSqlReader Metodu</span><span class="sxs-lookup"><span data-stu-id="b86ea-103">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="b86ea-104"><xref:System.Xml.XmlReader>Belirtilen akışı, ayarları ve ayrıştırma için bağlam bilgilerini kullanarak yeni bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b86ea-104">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="b86ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b86ea-105">Parameters</span></span>

- <span data-ttu-id="b86ea-106">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="b86ea-106">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="b86ea-107">XML verilerini içeren akış.</span><span class="sxs-lookup"><span data-stu-id="b86ea-107">The stream that contains the XML data.</span></span>

- <span data-ttu-id="b86ea-108">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="b86ea-108">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="b86ea-109">Yeni örnek için ayarlar <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="b86ea-109">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="b86ea-110">Bu değer olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="b86ea-110">This value can be `null`.</span></span>

- <span data-ttu-id="b86ea-111">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="b86ea-111">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="b86ea-112">XML parçasını ayrıştırmak için gereken bağlam bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b86ea-112">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="b86ea-113">Bu değer olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="b86ea-113">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="b86ea-114">Döndürülenler</span><span class="sxs-lookup"><span data-stu-id="b86ea-114">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="b86ea-115">Akıştaki XML verilerini okumak için kullanılan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b86ea-115">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="b86ea-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b86ea-116">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b86ea-117">`XmlReader.CreateSqlReader`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="b86ea-117">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b86ea-118">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b86ea-118">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b86ea-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b86ea-119">Requirements</span></span>

<span data-ttu-id="b86ea-120">**Ad alanı:**<xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="b86ea-120">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="b86ea-121">**Bütünleştirilmiş kod:** System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="b86ea-121">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="b86ea-122">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b86ea-122">**.NET Framework versions:** Available since 2.0.</span></span>
