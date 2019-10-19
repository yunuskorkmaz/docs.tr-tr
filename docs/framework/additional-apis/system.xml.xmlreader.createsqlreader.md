---
title: XmlReader. CreateSqlReader yöntemi (System. xml)
author: mairaw
ms.author: mairaw
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 302be4eff32d2c96a1571d291e0b289e77694db8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584136"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="f9167-102">XmlReader. CreateSqlReader yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9167-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="f9167-103">Belirtilen akışı, ayarları ve ayrıştırma için bağlam bilgilerini kullanarak yeni bir <xref:System.Xml.XmlReader> örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9167-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="f9167-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9167-104">Parameters</span></span>

- <span data-ttu-id="f9167-105">`input`<xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="f9167-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="f9167-106">XML verilerini içeren akış.</span><span class="sxs-lookup"><span data-stu-id="f9167-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="f9167-107">`settings`<xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="f9167-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="f9167-108">Yeni <xref:System.Xml.XmlReader> örneğinin ayarları.</span><span class="sxs-lookup"><span data-stu-id="f9167-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="f9167-109">Bu değer `null` olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9167-109">This value can be `null`.</span></span>

- <span data-ttu-id="f9167-110">`inputContext`<xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="f9167-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="f9167-111">XML parçasını ayrıştırmak için gereken bağlam bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f9167-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="f9167-112">Bu değer `null` olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9167-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="f9167-113">Döndürür</span><span class="sxs-lookup"><span data-stu-id="f9167-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="f9167-114">Akıştaki XML verilerini okumak için kullanılan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="f9167-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9167-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9167-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f9167-116">@No__t_0 yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9167-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f9167-117">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f9167-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9167-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9167-118">Requirements</span></span>

<span data-ttu-id="f9167-119">**Ad alanı:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="f9167-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="f9167-120">**Bütünleştirilmiş kod:** System. xml. dll</span><span class="sxs-lookup"><span data-stu-id="f9167-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="f9167-121">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9167-121">**.NET Framework versions:** Available since 2.0.</span></span>
