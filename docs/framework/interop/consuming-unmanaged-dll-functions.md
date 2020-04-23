---
title: Yönetilmeyen DLL İşlevlerini Kullanma
ms.date: 03/30/2017
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
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399975"
---
# <a name="consuming-unmanaged-dll-functions"></a>Yönetilmeyen DLL İşlevlerini Kullanma
Platform çağırma, yönetilen kodun, Windows API 'dakiler gibi dinamik bağlantı kitaplıkları (dll) içinde uygulanan yönetilmeyen işlevleri çağırmasına olanak sağlayan bir hizmettir. İçe aktarılmış bir işlevi bulur ve çağırır ve bağımsız değişkenlerini (tamsayılar, dizeler, diziler, yapılar vb.) gerektiğinde birlikte çalışma sınırında sıralar.  
  
 Bu bölüm, yönetilmeyen DLL işlevleri tüketen ilişkili görevleri tanıtır ve platform çağırma hakkında daha fazla bilgi sağlar. Aşağıdaki görevlere ek olarak, Genel hususlar ve ek bilgi ve örnekler sağlayan bir bağlantı vardır.  
  
#### <a name="to-consume-exported-dll-functions"></a>İçe aktarılmış DLL işlevlerini kullanmak için  
  
1. [DLL 'lerdeki Işlevleri belirler](identifying-functions-in-dlls.md).  
  
     En düşük düzeyde, işlevin adını ve onu içeren DLL adını belirtmeniz gerekir.  
  
2. [DLL işlevlerini barındıracak bir sınıf oluşturun](creating-a-class-to-hold-dll-functions.md).  
  
     Mevcut bir sınıfı kullanabilir, her yönetilmeyen işlev için tek bir sınıf oluşturabilir veya ilgili yönetilmeyen işlevler kümesini içeren bir sınıf oluşturabilirsiniz.  
  
3. [Yönetilen kodda prototipler oluşturun](creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] **Declare** ifadesini **Function** ve **lib** anahtar sözcükleriyle kullanın. Nadir bazı durumlarda, **paylaşılan işlev** anahtar sözcükleriyle **DllImportAttribute** kullanabilirsiniz. Bu durumlar bu bölümde daha sonra açıklanmaktadır.  
  
     Þ DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın. Yöntemi **static** ve **extern** değiştiricilere göre işaretleyin.  
  
     C++ DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın. Sarmalayıcı metodunu veya işlevi **extern "C"** ile işaretleyin.  
  
4. [BIR DLL Işlevi çağırın](calling-a-dll-function.md).  
  
     Yönetilen sınıfınıza, diğer yönetilen yöntemler gibi yöntemi çağırın. [Yapıları geçirme](passing-structures.md) ve [geri çağırma işlevlerini uygulama](callback-functions.md) özel durumlardır.  
  
 Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Platform çağırma ' ye daha yakından bakış  
 Platform çağırma, içe aktarılmış işlevleri bulmak ve çalışma zamanında bağımsız değişkenlerini sıralamak için meta verileri kullanır. Aşağıdaki çizim bu süreci göstermektedir.  
  
 ![Platform çağırma çağrısını gösteren diyagram.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Platform Invoke yönetilmeyen bir işlevi çağırdığında, aşağıdaki eylem dizisini gerçekleştirir:  
  
1. İşlevi içeren DLL 'yi bulur.  
  
2. DLL 'yi belleğe yükler.  
  
3. Bellekteki işlevin adresini bulur ve bağımsız değişkenlerini yığına iter, verileri gereken şekilde sıralama.  
  
    > [!NOTE]
    > DLL 'yi bulma ve yükleme ve bellekteki işlevin adresini bulma işlemi yalnızca işlevin ilk çağrısında gerçekleşir.  
  
4. Denetimi yönetilmeyen işleve aktarır.  
  
 Platform çağırma, yönetilmeyen işlev tarafından yönetilen çağırana oluşturulan özel durumları oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kod ile Birlikte Çalışma](index.md)
- [Platform Çağırma Örnekleri](platform-invoke-examples.md)
- [Birlikte Çalışma Hazırlama](interop-marshaling.md)
