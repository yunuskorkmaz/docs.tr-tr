---
title: s_isDebuggerCheckDisabledForTestPurposes alan
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name: System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location: PresentationCore.dll
api_type: Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.workload: dotnet
ms.openlocfilehash: 67da38d958d153ebe526f298785b39afb7be6513
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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

**Namespace:**<xref:System.Windows.Diagnostics>

**Derleme:** PresentationCore (içinde PresentationCore.dll)

**.NET framework sürümleri:** 4.6 sürümünden itibaren kullanılabilir.
