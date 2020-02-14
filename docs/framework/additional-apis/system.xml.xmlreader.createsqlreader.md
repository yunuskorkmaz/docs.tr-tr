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
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader Metodu

Belirtilen akışı, ayarları ve ayrıştırma için bağlam bilgilerini kullanarak yeni bir <xref:System.Xml.XmlReader> örneği oluşturur.

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametreler

- `input` <xref:System.IO.Stream>  
  XML verilerini içeren akış.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  Yeni <xref:System.Xml.XmlReader> örneğinin ayarları. Bu değer `null`olabilir.

- `inputContext` <xref:System.Xml.XmlParserContext>  
  XML parçasını ayrıştırmak için gereken bağlam bilgileri. Bu değer `null`olabilir.

## <a name="returns"></a>Döndürür

<xref:System.Xml.XmlReader>  
Akıştaki XML verilerini okumak için kullanılan bir nesne.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `XmlReader.CreateSqlReader` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Xml>

**Bütünleştirilmiş kod:** System. xml. dll

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
