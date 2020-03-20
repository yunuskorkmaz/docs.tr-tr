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
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader Metodu

Ayrıştırma <xref:System.Xml.XmlReader> için belirtilen akış, ayarlar ve bağlam bilgilerini kullanarak yeni bir örnek oluşturur.

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametreler

- `input` <xref:System.IO.Stream>  
  XML verilerini içeren akış.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  Yeni <xref:System.Xml.XmlReader> örneğin ayarları. Bu değer `null`.

- `inputContext` <xref:System.Xml.XmlParserContext>  
  XML parçasını ayrışdırmak için gereken bağlam bilgileri. Bu değer `null`.

## <a name="returns"></a>Döndürür

<xref:System.Xml.XmlReader>  
Akıştaki XML verilerini okumak için kullanılan bir nesne.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> Yöntem `XmlReader.CreateSqlReader` dahilidir ve doğrudan kodunuzda kullanılmak üzere değildir.
>
> Microsoft, bu yöntemin hiçbir koşulda bir üretim uygulamasında kullanılmasını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Xml>

**Montaj:** System.xml.dll

**.NET Framework sürümleri:** 2.0'dan beri mevcuttur.
