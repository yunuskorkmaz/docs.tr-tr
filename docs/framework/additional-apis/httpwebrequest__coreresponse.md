---
title: HttpWebRequest. _CoreResponse alanı
description: .NET 'teki HttpWebRequest. _CoreResponse alanı hakkında bilgi edinin. Bu alan, HTTP yanıtı ayrıştırma sonucunu içeren bir CoreResponseData veya Exception nesnesidir.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989752"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest. \_ CoreResponse alanı

`HttpWebRequest._CoreResponse`HTTP yanıtı ayrıştırma sonucunu içeren bir nesne (bir [CoreResponseData](coreresponsedata.md) veya a <xref:System.Exception> ).

## <a name="syntax"></a>Syntax
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu. Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın. Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
