---
title: "Yönetilmeyen DLL İşlevlerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec93728566d6aa16d4b9b15b171d79831cc0dbeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-unmanaged-dll-functions"></a>Yönetilmeyen DLL İşlevlerini Kullanma
Platform çağırma etkinleştirir Win32 API de gibi dinamik bağlantı kitaplıklarını (DLL'ler), uygulanan yönetilmeyen işlevleri çağırmak için kodu yönetilen bir hizmettir. Verilen işlevi çağırır bulur ve bağımsız değişkenleri (tamsayı, dize, diziler, yapıları ve benzeri) arasında birlikte çalışabilirlik sınır gerektiği şekilde sıralar. Bu hizmet hakkında daha fazla bilgi için bkz: [A daha yakın bakabilir Platform Çağırma](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).  
  
 Bu bölüm, yönetilmeyen DLL işlevlerini kullanma ile ilgili çeşitli görevleri tanıtır. Aşağıdaki görevlere ek olarak, genel konular ve ek bilgi ve örnekler sağlayan bir bağlantı vardır.  
  
#### <a name="to-consume-exported-dll-functions"></a>Dışa aktarılan DLL işlevleri kullanmak için  
  
1.  [DLL'lerde işlevleri tanımlamak](../../../docs/framework/interop/identifying-functions-in-dlls.md).  
  
     En azından adını işlevi ve içerdiği DLL adını belirtmeniz gerekir.  
  
2.  [DLL işlevleri için bir sınıf oluşturun](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).  
  
     Varolan bir sınıf kullanma, yönetilmeyen her işlev için tek bir sınıf oluşturun veya ilgili yönetilmeyen işlevler kümesi içeren bir sınıf oluşturun.  
  
3.  [Yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Kullanım **Declare** deyimiyle **işlevi** ve **Lib** anahtar sözcükler. Bazı nadir durumlarda, kullandığınız **DllImportAttribute** ile **paylaşılan işlevi** anahtar sözcükler. Bu durumlarda, daha sonra bu bölümde açıklanmıştır.  
  
     [C#] Kullanım **DllImportAttribute** işlevini ve DLL tanımlamak için. Yöntemiyle işaretlemek **statik** ve **extern** değiştiricileri.  
  
     [C++] Kullanım **DllImportAttribute** işlevini ve DLL tanımlamak için. Sarmalayıcı yöntemini işaretlemek veya ile işlev **extern "C"**.  
  
4.  [Bir DLL işlevi çağırma](../../../docs/framework/interop/calling-a-dll-function.md).  
  
     Yönetilen herhangi bir yöntemini gibi yönetilen sınıfınız yöntemini çağırın. [Yapıları geçirme](../../../docs/framework/interop/passing-structures.md) ve [geri çağırma işlevlerini uygulama](../../../docs/framework/interop/callback-functions.md) özel durumları olan.  
  
 Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Yakından platform çağırma  
 Platform çağırma dışarı aktarılan işlevleri bulun ve çalışma zamanında kendi bağımsız değişkenleri hazırlamak için meta verileri kullanır. Aşağıdaki çizim bu süreci göstermektedir.  
  
 ![Platform Çağırma](../../../docs/framework/interop/media/pinvoke.gif "PInvoke")  
Yönetilmeyen DLL işlev çağrısı bir platform çağırma  
  
 Ne zaman platform çağırma yönetilmeyen bir işlevi çağırdığı sırasıyla aşağıdaki eylemleri gerçekleştirir:  
  
1.  İşlevi içeren DLL bulur.  
  
2.  DLL belleğe yükler.  
  
3.  İşlevin adresini bellekte bulur ve bağımsız değişkenlerini verileri gereken şekilde hazırlama yığına iter.  
  
    > [!NOTE]
    >  Bulma ve dll dosyasını yüklerken ve bellekte işlevin adresini bulmak işlevi yalnızca ilk çağrıda oluşur.  
  
4.  Yönetilmeyen işlev aktarımları denetimi.  
  
 Platform çağırma yönetilen çağırana yönetilmeyen işlevi tarafından oluşturulan atar özel durumları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen kod ile birlikte çalışma](../../../docs/framework/interop/index.md)  
 [Platform çağırma örnekleri](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)  
 [Yönetilmeyen DLL işlevlerini kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
