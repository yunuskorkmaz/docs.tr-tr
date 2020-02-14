---
title: Message. WriteStartHeaders yöntemi (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214873"
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
