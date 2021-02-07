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
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader Metodu

<xref:System.Xml.XmlReader>Belirtilen akışı, ayarları ve ayrıştırma için bağlam bilgilerini kullanarak yeni bir örnek oluşturur.

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametreler

- `input` <xref:System.IO.Stream>  
  XML verilerini içeren akış.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  Yeni örnek için ayarlar <xref:System.Xml.XmlReader> . Bu değer olabilir `null` .

- `inputContext` <xref:System.Xml.XmlParserContext>  
  XML parçasını ayrıştırmak için gereken bağlam bilgileri. Bu değer olabilir `null` .

## <a name="returns"></a>Döndürülenler

<xref:System.Xml.XmlReader>  
Akıştaki XML verilerini okumak için kullanılan bir nesne.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `XmlReader.CreateSqlReader`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Xml>

**Bütünleştirilmiş kod:** System.Xml.dll

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
