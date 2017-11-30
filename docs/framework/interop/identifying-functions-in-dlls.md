---
title: "DLL'lerde İşlevleri Tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b5aa725d30e280d672724c7b7f4fd11a848a3ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="identifying-functions-in-dlls"></a>DLL'lerde İşlevleri Tanımlama
DLL işlevini kimliğini aşağıdaki öğelerden oluşur:  
  
-   İşlev adı veya sıra  
  
-   Uygulama bulunabilir DLL dosyasının adı  
  
 Örneğin, belirten **MessageBox** User32.dll işlevinde işlevi tanımlar (**MessageBox**) ve konumunu (User32.dll, User32 veya user32). Microsoft Windows uygulama programlama arabirimi (Win32 API) karakterleri ve dizeleri işleme her işlev iki sürümü içerebilir: 1-bayt karakter ANSI sürümü ve 2-bayt karakter Unicode sürümü. Karakter kümesi belirtilmemiş olduğunda temsil ettiği <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> alan, ANSI varsayılanlara. Bazı işlevler ikiden fazla sürümleri olabilir.  
  
 **MessageBoxA** ANSI giriş noktası için **MessageBox** işlev; **MessageBoxW** Unicode sürümüdür. Çeşitli komut satırı araçları çalıştırarak user32.dll gibi belirli bir DLL için işlev adlarını listeleyebilirsiniz. Örneğin, kullanabileceğiniz `dumpbin /exports user32.dll` veya `link /dump /exports user32.dll` işlev adları elde edilir.  
  
 DLL özgün giriş noktası için yeni bir ad eşleme sürece ne olursa olsun, kodunuzun içinde ister yönetilmeyen işlev yeniden adlandırabilirsiniz. Yönetilen kaynak kodunda yönetilmeyen DLL işlev yeniden adlandırma ile ilgili yönergeler için bkz: [giriş noktası belirtme](../../../docs/framework/interop/specifying-an-entry-point.md).  
  
 Platform çağırma etkinleştirir çağırarak işletim sisteminin önemli bir kısmını denetlemek için işlevleri Win32 API ve diğer DLL'ler. Win32 API yanı sıra platformu aracılığıyla kullanılabilir DLL'ler çağırma ve diğer pek çok API'leri vardır.  
  
 Aşağıdaki tabloda bazı yaygın olarak kullanılan dll dosyaları Win32 API içinde açıklanmaktadır.  
  
|DLL|İçeriği açıklaması|  
|---------|-----------------------------|  
|GDI32.dll|Grafik cihaz arabirimi (GDI) işlevleri çıktı çizim ve yazı tipi yönetimi için olanlar gibi cihaz için.|  
|Kernel32.dll|Bellek yönetimi ve kaynak işleme için alt düzey işletim sistemi işlevleri.|  
|User32.dll|İleti işleme, zamanlayıcılar, menüleri ve iletişim için Windows Yönetim işlevleri.|  
  
 Win32 API üzerindeki tüm belgeler için bkz. Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen DLL işlevlerini kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [Giriş noktası belirtme](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [DLL işlevleri için bir sınıf oluşturma](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [Yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [DLL işlevini çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
