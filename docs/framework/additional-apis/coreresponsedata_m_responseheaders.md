---
title: CoreResponseData. m_ResponseHeaders alanı
description: .NET 'teki CoreResponseData. m_ResponseHeaders alanını anlayın. Bu alan, sunucu yanıtıyla ilişkili üst bilgilerin bulunduğu bir WebHeaderCollection türüdür.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 7c7b896193cb81e9fc9e3ec28110359003a36728
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989787"
---
# <a name="coreresponsedatam_responseheaders-field"></a>CoreResponseData. d \_ ResponseHeaders alanı

`CoreResponseData.m_ResponseHeaders`, <xref:System.Net.WebHeaderCollection> sunucu yanıtıyla ilişkili üst bilgilerden oluşur.

## <a name="syntax"></a>Syntax
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu. Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın. Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
