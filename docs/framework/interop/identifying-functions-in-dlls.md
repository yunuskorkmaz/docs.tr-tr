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
ms.openlocfilehash: 1a94bb2020b07ba8405d901f46ec4a0687e79700
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121970"
---
# <a name="identifying-functions-in-dlls"></a>DLL'lerde İşlevleri Tanımlama
DLL işlevinin kimliği aşağıdaki öğelerden oluşur:  
  
- İşlev adı veya sıra sayısı  
  
- Uygulamanın bulunduğu DLL dosyasının adı  
  
 Örneğin, User32. dll ' de **MessageBox** işlevini belirtmek, Işlevi (**MessageBox**) ve konumunu (User32. dll, User32 veya User32) belirler. Microsoft Windows uygulama programlama arabirimi (Windows API), karakterleri ve dizeleri işleyen her bir işlevin iki sürümünü içerebilir: 1 baytlık karakter ANSI sürümü ve 2 baytlık karakter Unicode sürümü. Belirtilmediğinde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> alan tarafından temsil edilen karakter kümesi varsayılan olarak ANSI olur. Bazı işlevlerin ikiden fazla sürümü olabilir.  
  
 **MessageBoxA** , **MESSAGEBOX** işlevi için ANSI giriş noktasıdır; **MessageBoxW** Unicode sürümüdür. Çeşitli komut satırı araçlarını çalıştırarak, User32. dll gibi belirli bir DLL için işlev adlarını listeleyebilirsiniz. Örneğin, işlev adlarını almak için `dumpbin /exports user32.dll` veya `link /dump /exports user32.dll` kullanabilirsiniz.  
  
 Yeni adı DLL 'deki özgün giriş noktasına eşledikten sonra, yönetilmeyen bir işlevi kodunuzda dilediğiniz şekilde yeniden adlandırabilirsiniz. Yönetilen kaynak kodunda yönetilmeyen DLL işlevini yeniden adlandırma yönergeleri için bkz. [giriş noktası belirtme](specifying-an-entry-point.md).  
  
 Platform çağırma, Windows API ve diğer dll 'Lerdeki işlevleri çağırarak işletim sisteminin önemli bir bölümünü denetlemenize olanak sağlar. Windows API 'sine ek olarak, platform Invoke aracılığıyla kullanabileceğiniz çok sayıda başka API ve DLL vardır.  
  
 Aşağıdaki tabloda, Windows API 'sinde yaygın olarak kullanılan birkaç dll açıklanmaktadır.  
  
|DLL|Içeriklerin açıklaması|  
|---------|-----------------------------|  
|GDI32. dll|Çizim ve yazı tipi yönetimi gibi cihaz çıktıları için Grafik Cihaz Arabirimi (GDI) işlevleri.|  
|Kernel32. dll|Bellek yönetimi ve kaynak işleme için alt düzey işletim sistemi işlevleri.|  
|User32. dll|İleti işleme, zamanlayıcılar, menüler ve iletişimler için Windows yönetim işlevleri.|  
  
 Windows API 'SI ile ilgili tüm belgeler için bkz. Platform SDK 'Sı. Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)
- [Giriş Noktası Belirtme](specifying-an-entry-point.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](creating-a-class-to-hold-dll-functions.md)
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
