---
title: Message. WriteStartHeaders yöntemi (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: a2c82ee4029c7af0396219f5ded8c999fd01d65b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451180"
---
# <a name="messagewritestartheaders-method"></a>Message. WriteStartHeaders yöntemi

Başlangıç üstbilgisini, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> yöntemini çağırarak bir XML dosyasına yazar.

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>Parametreler

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Başlangıç üst bilgisini bir XML dosyasına yazmak için kullanılan yazıcı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `Message.WriteStartHeaders` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.ServiceModel.Channels>

**Bütünleştirilmiş kod:** System. ServiceModel. dll

**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.
