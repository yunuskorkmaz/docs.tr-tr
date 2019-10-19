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
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader. CreateSqlReader yöntemi

Belirtilen akışı, ayarları ve ayrıştırma için bağlam bilgilerini kullanarak yeni bir <xref:System.Xml.XmlReader> örneği oluşturur.

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametreler

- `input`<xref:System.IO.Stream>  
  XML verilerini içeren akış.

- `settings`<xref:System.Xml.XmlReaderSettings>  
  Yeni <xref:System.Xml.XmlReader> örneğinin ayarları. Bu değer `null` olabilir.

- `inputContext`<xref:System.Xml.XmlParserContext>  
  XML parçasını ayrıştırmak için gereken bağlam bilgileri. Bu değer `null` olabilir.

## <a name="returns"></a>Döndürür

<xref:System.Xml.XmlReader>  
Akıştaki XML verilerini okumak için kullanılan bir nesne.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t_0 yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Xml>

**Bütünleştirilmiş kod:** System. xml. dll

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
