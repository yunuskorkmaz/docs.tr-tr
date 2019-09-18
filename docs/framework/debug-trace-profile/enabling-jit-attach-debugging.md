---
title: JIT-Ekleme Hata Ayıklamayı Etkinleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052833"
---
# <a name="enabling-jit-attach-debugging"></a>JIT-Ekleme Hata Ayıklamayı Etkinleştirme
JıT-Attach hata ayıklaması, hatalar ile ilgili bir hata ayıklayıcıyı bir işleme iliştirirken veya belirli yöntemler veya işlevler tarafından tetikleniyorsa kullanılan tümceciktir.  
  
 JıT-Attach hata ayıklaması aşağıdaki hata koşulları altında kullanılır:  
  
- İşlenmemiş özel durumlar (hem yerel hem de yönetilen kodda).  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Method veya [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) Işlevi (Windows 7 ailesi).  
  
- Çalışma zamanı önemli hataları.  
  
 JıT-Attach hata ayıklaması, aşağıdaki yöntemler ve işlevlere yapılan çağrılar tarafından da tetiklenir:  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>yöntemidir.  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>yöntemidir.  
  
- [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) Işlevi (Win32).  
  
 .NET Framework 4 ' den önce, .NET Framework yerel ve yönetilen hata ayıklayıcıların davranışını denetlemek için ayrı kayıt defteri anahtarları sağladı. .NET Framework 4 ' te başlayarak, Denetim tek bir kayıt defteri anahtarı altında birleştirilir: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Bu anahtar için ayarlayabileceğiniz değerler, bir hata ayıklayıcının çağrılıp çağrılmadığını ve varsa Kullanıcı etkileşimi gerektiren bir iletişim kutusuyla çağrılması gerektiğini belirtir. Bu kayıt defteri anahtarını ayarlama hakkında daha fazla bilgi için bkz. [otomatik hata ayıklamayı yapılandırma](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama, İzleme ve Profil Oluşturma](index.md)
- [Görüntüde Hata Ayıklamayı Kolaylaştırma](making-an-image-easier-to-debug.md)
