---
title: HttpWebRequest. _CoreResponse alanı
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
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740453"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest.\_CoreResponse alanı

`HttpWebRequest._CoreResponse`, HTTP yanıtı ayrıştırma sonucunu içeren bir nesnedir (bir [CoreResponseData](coreresponsedata.md) veya <xref:System.Exception>).

## <a name="syntax"></a>Sözdizimi
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu. Bunun yerine, ağ kodunu bağlamak için bir <xref:System.Diagnostics.DiagnosticSource> kullanmanız gerekir. Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
> 
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System. dll içinde)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
