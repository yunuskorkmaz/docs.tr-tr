---
title: XmlReader.CreateSqlReader Yöntemi (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155745"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="b7eae-102">XmlReader.CreateSqlReader Metodu</span><span class="sxs-lookup"><span data-stu-id="b7eae-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="b7eae-103">Ayrıştırma <xref:System.Xml.XmlReader> için belirtilen akış, ayarlar ve bağlam bilgilerini kullanarak yeni bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7eae-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="b7eae-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7eae-104">Parameters</span></span>

- <span data-ttu-id="b7eae-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="b7eae-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="b7eae-106">XML verilerini içeren akış.</span><span class="sxs-lookup"><span data-stu-id="b7eae-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="b7eae-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="b7eae-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="b7eae-108">Yeni <xref:System.Xml.XmlReader> örneğin ayarları.</span><span class="sxs-lookup"><span data-stu-id="b7eae-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="b7eae-109">Bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="b7eae-109">This value can be `null`.</span></span>

- <span data-ttu-id="b7eae-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="b7eae-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="b7eae-111">XML parçasını ayrışdırmak için gereken bağlam bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b7eae-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="b7eae-112">Bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="b7eae-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="b7eae-113">Döndürür</span><span class="sxs-lookup"><span data-stu-id="b7eae-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="b7eae-114">Akıştaki XML verilerini okumak için kullanılan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b7eae-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7eae-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7eae-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b7eae-116">Yöntem `XmlReader.CreateSqlReader` dahilidir ve doğrudan kodunuzda kullanılmak üzere değildir.</span><span class="sxs-lookup"><span data-stu-id="b7eae-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b7eae-117">Microsoft, bu yöntemin hiçbir koşulda bir üretim uygulamasında kullanılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b7eae-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7eae-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7eae-118">Requirements</span></span>

<span data-ttu-id="b7eae-119">**Ad alanı:**<xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="b7eae-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="b7eae-120">**Montaj:** System.xml.dll</span><span class="sxs-lookup"><span data-stu-id="b7eae-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="b7eae-121">**.NET Framework sürümleri:** 2.0'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b7eae-121">**.NET Framework versions:** Available since 2.0.</span></span>
