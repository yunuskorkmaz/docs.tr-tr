---
description: 'Hakkında daha fazla bilgi edinin: s_isDebuggerCheckDisabledForTestPurposes alanı'
title: s_isDebuggerCheckDisabledForTestPurposes alanı
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: a71235c13a7a35872bcf5374be8077bafad5ff9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802664"
---
# <a name="s_isdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes alanı

Sınıftaki bu özel alan `System.Windows.Diagnostics.VisualDiagnostics` , Visual Studio tarafından etkin bir hata ayıklayıcı için iç denetim yapılıp yapılmayacağını anlamak üzere kullanılır.

## <a name="syntax"></a>Syntax

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> Sınıftaki API 'Ler `System.Windows.Diagnostics.VisualDiagnostics` yalnızca bir uygulama hata ayıklayıcı altında çalışırken kullanılabilir. `s_isDebuggerCheckDisabledForTestPurposes` `true` Bir hata ayıklayıcı dışında API 'lere erişmek için olarak ayarlayın.
>
> Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Windows.Diagnostics>

**Bütünleştirilmiş kod:** PresentationCore (PresentationCore.dll)

**.NET Framework sürümleri:** 4,6 sürümünden itibaren kullanılabilir.
