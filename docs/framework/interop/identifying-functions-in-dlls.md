---
title: DLL'lerde İşlevleri Tanımlama
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb1aba9e794928b0eb905722e2a5d7df84100ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729216"
---
# <a name="identifying-functions-in-dlls"></a>DLL'lerde İşlevleri Tanımlama
Bir DLL işlevini kimliğini aşağıdaki öğelerden oluşur:  
  
-   İşlev adı veya sıra  
  
-   Uygulama bulunabilir DLL dosyasının adı  
  
 Örneğin, belirten **MessageBox** User32.dll işlevinde işlevi tanımlar (**MessageBox**) ve konumu (User32.dll, User32 veya user32). Microsoft Windows uygulama programlama arabirimi (Win32 API) karakterleri ve dizeleri işleyen her işlevin iki sürümü içermelidir: 1-bayt karakter ANSI sürümü ve 2-bayt karakter Unicode sürümü. Belirtilmediğinde, karakter kümesini temsil ettiği <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> ANSI varsayılan alan. Bazı işlevler, ikiden fazla sürümleri olabilir.  
  
 **MessageBoxA** ANSI giriş noktası için **MessageBox** işlev; **MessageBoxW** Unicode sürümüdür. İşlev adları, user32.dll gibi belirli bir DLL için çeşitli komut satırı araçları'nı çalıştırarak listeleyebilirsiniz. Örneğin, kullanabileceğiniz `dumpbin /exports user32.dll` veya `link /dump /exports user32.dll` işlev adlarını elde edilir.  
  
 Yönetilmeyen bir işlev özgün DLL giriş noktası için yeni adı eşleme sürece kodunuzun içinde dilediğiniz şekilde yeniden adlandırabilirsiniz. Yönetilen kaynak kodunda bir yönetilmeyen DLL işlevi yeniden adlandırma ile ilgili yönergeler için bkz: [giriş noktası belirtme](../../../docs/framework/interop/specifying-an-entry-point.md).  
  
 Platform çağırma etkinleştirir Win32 API ve diğer DLL'leri çağırarak işletim sisteminin önemli bir bölümünü denetlemenizi işlevleri. Win32 API yanı sıra diğer birçok API vardır ve platformu kullanılabilir DLL'ler çağırın.  
  
 Aşağıdaki tablo bazı yaygın olarak kullanılan dll dosyaları Win32 API açıklar.  
  
|DLL|İçeriği açıklaması|  
|---------|-----------------------------|  
|GDI32.dll|Grafik cihaz arabirimi (GDI) işlevleri için çıktı çizme ve yazı tipi Yönetim için olanlar gibi cihaz.|  
|Kernel32.dll|Bellek yönetimi ve kaynak işleme işlevleri alt düzey işletim sistemi.|  
|User32.dll|İleti işleme, zamanlayıcıları, menüler ve iletişim için Windows Yönetim işlevleri.|  
  
 Win32 API ile ilgili kapsamlı belgeler için bkz. Nasıl oluşturulacağını gösteren örnekler için. NET tabanlı bildirimler platformuyla kullanılacak çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen DLL İşlevlerini Kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [Giriş Noktası Belirtme](../../../docs/framework/interop/specifying-an-entry-point.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)
- [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
