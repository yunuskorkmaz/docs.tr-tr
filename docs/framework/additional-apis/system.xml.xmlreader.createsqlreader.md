---
title: XmlReader. CreateSqlReader yöntemi (System. xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: c65ef7c073175488c11c5e912a44d46fd4319209
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215457"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="f06f6-102">XmlReader.CreateSqlReader Metodu</span><span class="sxs-lookup"><span data-stu-id="f06f6-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="f06f6-103">Belirtilen akışı, ayarları ve ayrıştırma için bağlam bilgilerini kullanarak yeni bir <xref:System.Xml.XmlReader> örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f06f6-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="f06f6-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f06f6-104">Parameters</span></span>

- <span data-ttu-id="f06f6-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="f06f6-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="f06f6-106">XML verilerini içeren akış.</span><span class="sxs-lookup"><span data-stu-id="f06f6-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="f06f6-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="f06f6-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="f06f6-108">Yeni <xref:System.Xml.XmlReader> örneğinin ayarları.</span><span class="sxs-lookup"><span data-stu-id="f06f6-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="f06f6-109">Bu değer `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="f06f6-109">This value can be `null`.</span></span>

- <span data-ttu-id="f06f6-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="f06f6-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="f06f6-111">XML parçasını ayrıştırmak için gereken bağlam bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f06f6-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="f06f6-112">Bu değer `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="f06f6-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="f06f6-113">Döndürür</span><span class="sxs-lookup"><span data-stu-id="f06f6-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="f06f6-114">Akıştaki XML verilerini okumak için kullanılan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="f06f6-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f06f6-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f06f6-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f06f6-116">`XmlReader.CreateSqlReader` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f06f6-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f06f6-117">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f06f6-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f06f6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f06f6-118">Requirements</span></span>

<span data-ttu-id="f06f6-119">**Ad alanı:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="f06f6-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="f06f6-120">**Bütünleştirilmiş kod:** System. xml. dll</span><span class="sxs-lookup"><span data-stu-id="f06f6-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="f06f6-121">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f06f6-121">**.NET Framework versions:** Available since 2.0.</span></span>
