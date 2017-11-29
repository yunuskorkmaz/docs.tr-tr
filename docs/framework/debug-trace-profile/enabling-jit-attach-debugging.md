---
title: "JIT-Ekleme Hata Ayıklamayı Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 107b47ba8abcbd1084bed6e043f5a648aa91cc91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-jit-attach-debugging"></a>JIT-Ekleme Hata Ayıklamayı Etkinleştirme
JIT-ekleme hata ayıklama hatalarla ya da belirli yöntemler ve işlevlere tarafından tetiklenebilir bir hata ayıklayıcısı bir işlemine iliştirme tanımlamak için kullanılan terimdir.  
  
 JIT-ekleme hata ayıklama, aşağıdaki hata koşullar altında kullanılır:  
  
-   İşlenmemiş özel durumlardan (yerel ve yönetilen kod).  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=nameWithType>yöntem veya [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) işlevi (Windows 7 ailesi).  
  
-   Çalışma zamanı önemli hataları.  
  
 JIT-ekleme hata ayıklama işlevleri ve aşağıdaki yöntemlerden yapılan çağrılar tarafından da tetiklenir:  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>yöntem.  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>yöntem.  
  
-   [DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) işlevi (Win32).  
  
 Önce [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework yerel ve yönetilen hata ayıklayıcıları davranışını denetlemek için ayrı kayıt defteri anahtarlarını sağlanan. İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], denetimi altında bir tek kayıt defteri anahtarını birleştirilmiş: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Bu anahtar için ayarlayabileceğiniz değerler bir hata ayıklayıcısı çağrılır, ve olup kullanıcı etkileşimi gerektiren bir iletişim kutusuyla çağrılması gerekiyorsa, olup olmadığını belirler. Bu kayıt defteri anahtarı ayarlama hakkında daha fazla bilgi için bkz: [otomatik hata ayıklama yapılandırma](http://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama, izleme ve profil oluşturma](../../../docs/framework/debug-trace-profile/index.md)  
 [Bir görüntü hata ayıklamayı kolaylaştırma](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [Profil oluşturma etkinleştirme](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)
