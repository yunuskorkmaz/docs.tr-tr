---
title: s_isDebuggerCheckDisabledForTestPurposes alanı
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: b6490919163a7c4a618bf9a8d0e2aa145f60eda1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372314"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes alanı

Bu özel bir alanda `System.Windows.Diagnostics.VisualDiagnostics` sınıfı için bir etkin hata ayıklayıcı iç bir onay gerçekleştirip gerçekleştirmediğini belirlemek için Visual Studio tarafından kullanılır.

## <a name="syntax"></a>Sözdizimi

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> API'leri `System.Windows.Diagnostics.VisualDiagnostics` sınıfı bulunan ve yalnızca bir uygulama hata ayıklayıcı altında çalışırken. Ayarlama `s_isDebuggerCheckDisabledForTestPurposes` için `true` API'lere bir hata ayıklayıcı dışında.
>
> Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Windows.Diagnostics>

**Derleme:** PresentationCore (içinde PresentationCore.dll)

**.NET framework sürümleri:** 4.6 sonrasında kullanılabilir.