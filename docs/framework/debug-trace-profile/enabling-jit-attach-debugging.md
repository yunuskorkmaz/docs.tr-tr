---
title: JIT-Ekleme Hata Ayıklamayı Etkinleştirme
description: Hatalarla karşılaştığınızda bir işleme hata ayıklayıcı eklemek için tam zamanında (JıT) iliştirme hata ayıklamayı etkinleştirin. Belirli yöntemler veya işlevler tarafından tetiklenebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416050"
---
# <a name="enabling-jit-attach-debugging"></a>JIT-Ekleme Hata Ayıklamayı Etkinleştirme
JıT-Attach hata ayıklaması, hatalar ile ilgili bir hata ayıklayıcıyı bir işleme iliştirirken veya belirli yöntemler veya işlevler tarafından tetikleniyorsa kullanılan tümceciktir.  
  
 JıT-Attach hata ayıklaması aşağıdaki hata koşulları altında kullanılır:  
  
- İşlenmemiş özel durumlar (hem yerel hem de yönetilen kodda).  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Method veya [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) Işlevi (Windows 7 ailesi).  
  
- Çalışma zamanı önemli hataları.  
  
 JıT-Attach hata ayıklaması, aşağıdaki yöntemler ve işlevlere yapılan çağrılar tarafından da tetiklenir:  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>yöntemidir.  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>yöntemidir.  
  
- [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Işlevi (Win32).  
  
 .NET Framework 4 ' den önce, .NET Framework yerel ve yönetilen hata ayıklayıcıların davranışını denetlemek için ayrı kayıt defteri anahtarları sağladı. .NET Framework 4 ' te başlayarak, Denetim tek bir kayıt defteri anahtarı altında birleştirilir: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Bu anahtar için ayarlayabileceğiniz değerler, bir hata ayıklayıcının çağrılıp çağrılmadığını ve varsa Kullanıcı etkileşimi gerektiren bir iletişim kutusuyla çağrılması gerektiğini belirtir. Bu kayıt defteri anahtarını ayarlama hakkında daha fazla bilgi için bkz. [otomatik hata ayıklamayı yapılandırma](/windows/win32/debug/configuring-automatic-debugging).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama, Izleme ve profil oluşturma](index.md)
- [Görüntüde Hata Ayıklamayı Kolaylaştırma](making-an-image-easier-to-debug.md)
