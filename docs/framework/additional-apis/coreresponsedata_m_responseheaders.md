---
title: CoreResponseData.m_ResponseHeaders alanı
description: .NET 'teki CoreResponseData.m_ResponseHeaders alanını anlayın. Bu alan, sunucu yanıtıyla ilişkili üst bilgilerin bulunduğu bir WebHeaderCollection türüdür.
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
ms.openlocfilehash: 6e0203094376de6ec2870649dd3c025e88639bb8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875934"
---
# <a name="coreresponsedatam_responseheaders-field"></a>CoreResponseData. d \_ ResponseHeaders alanı

`CoreResponseData.m_ResponseHeaders` , <xref:System.Net.WebHeaderCollection> sunucu yanıtıyla ilişkili üst bilgilerden oluşur.

## <a name="syntax"></a>Syntax
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu. Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın. Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
