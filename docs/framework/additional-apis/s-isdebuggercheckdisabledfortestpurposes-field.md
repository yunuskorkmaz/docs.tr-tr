---
title: s_isDebuggerCheckDisabledForTestPurposes alan
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
robots: noindex,nofollow
ms.openlocfilehash: fbbd8d33ea163efaad1417ab4a1435df729e4897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752214"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes alan

Bu özel alanı `System.Windows.Diagnostics.VisualDiagnostics` sınıfı, bir iç onay etkin hata ayıklayıcı için gerçekleştirilen olup olmadığını belirlemek için Visual Studio tarafından kullanılır.

## <a name="syntax"></a>Sözdizimi
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  API ın `System.Windows.Diagnostics.VisualDiagnostics` sınıfı yalnızca bir uygulama bir hata ayıklayıcı altında çalıştığı durumlarda kullanılabilir. Ayarlama `s_isDebuggerCheckDisabledForTestPurposes` için `true` bir hata ayıklayıcı dışında API'leri erişmek için.  
>   
>  Microsoft hiçbir koşulda bir üretim uygulamasında bu alan kullanımını desteklemez.  

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Windows.Diagnostics>

**Derleme:** PresentationCore (içinde PresentationCore.dll)

**.NET framework sürümleri:** 4.6 sürümünden itibaren kullanılabilir.
