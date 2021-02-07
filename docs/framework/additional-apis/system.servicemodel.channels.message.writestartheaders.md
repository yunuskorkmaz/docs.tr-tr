---
description: 'Daha fazla bilgi edinin: Message. WriteStartHeaders yöntemi'
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
ms.openlocfilehash: 20cadf5f1eecf6d8e02c5dc4597889abaef4ec36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699369"
---
# <a name="messagewritestartheaders-method"></a>Message. WriteStartHeaders yöntemi

Yöntemini çağırarak başlangıç üstbilgisini bir XML dosyasına yazar <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> .

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>Parametreler

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Başlangıç üst bilgisini bir XML dosyasına yazmak için kullanılan yazıcı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `Message.WriteStartHeaders`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.ServiceModel.Channels>

**Bütünleştirilmiş kod:** System.ServiceModel.dll

**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.
