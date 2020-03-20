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
Platform çağırma, yönetilen kodun Windows API'dakiler gibi dinamik bağlantı kitaplıklarında (DL'lerde) uygulanan yönetilmeyen işlevleri çağırmasını sağlayan bir hizmettir. Dışa aktarılan bir işlevi bulur ve çağırır ve gerektiğinde interişlem sınırı boyunca bağımsız değişkenlerini (karşıtlar, dizeleri, diziler, yapılar vb.) sıralar.  
  
 Bu bölümde, yönetilmeyen DLL işlevlerinin tüketilmesiyle ilişkili görevler tanıtılmış ve platform çağırma hakkında daha fazla bilgi verilmektedir. Aşağıdaki görevlere ek olarak, genel hususlar ve ek bilgi ve örnekler sağlayan bir bağlantı vardır.  
  
#### <a name="to-consume-exported-dll-functions"></a>Dışa aktarılan DLL işlevlerini tüketmek için  
  
1. [DLs işlevlerini tanımlayın.](identifying-functions-in-dlls.md)  
  
     En az düzeyde, işlevin adını ve onu içeren DLL'nin adını belirtmeniz gerekir.  
  
2. [DLL işlevlerini tutmak için bir sınıf oluşturun.](creating-a-class-to-hold-dll-functions.md)  
  
     Varolan bir sınıfı kullanabilir, her yönetilmeyen işlev için ayrı bir sınıf oluşturabilir veya ilgili yönetilmeyen işlevler kümesi içeren bir sınıf oluşturabilirsiniz.  
  
3. [Yönetilen kodda prototipler oluşturun.](creating-prototypes-in-managed-code.md)  
  
     [Visual Basic] **İşlev** ve **Lib** anahtar kelimeleriyle **Bildir ifadesini** kullanın. Bazı nadir durumlarda, **Paylaşılan İşlev** anahtar kelimeleri ile **DllImportAttribute** kullanabilirsiniz. Bu olgular daha sonra bu bölümde açıklanmıştır.  
  
     [C#] DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın. Yöntemi **statik** ve **extern** değiştiriciler ile işaretleyin.  
  
     [C++] DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın. Sarma makinesi yöntemini veya işlevini **extern "C"** ile işaretleyin.  
  
4. [Bir DLL işlevini arayın.](calling-a-dll-function.md)  
  
     Yönetilen sınıfınızdaki yöntemi, diğer yönetilen yöntemlerde olduğu gibi arayın. [Yapıları n geçirilmesi](passing-structures.md) ve [geri arama işlevlerinin uygulanması](callback-functions.md) özel durumlardır.  
  
 Nasıl inşa edilebildiğini gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, [Bkz. Platform Invoke ile Verileri Mareşalleme.](marshaling-data-with-platform-invoke.md)  
  
## <a name="a-closer-look-at-platform-invoke"></a>Platform çağırmaya daha yakından bakmak  
 Platform, dışa aktarılan işlevleri bulmak ve bağımsız değişkenlerini çalışma zamanında mareşallemek için meta verilere dayanır. Aşağıdaki çizim bu süreci göstermektedir.  
  
 ![Platform çağrısı çağrısını gösteren diyagram.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Platform yönetilmeyen bir işlev çağırdığında, aşağıdaki eylem sırasını gerçekleştirir:  
  
1. İşleviçeren DLL'yi bulur.  
  
2. DLL'yi belleğe yükler.  
  
3. Bellekteki işlevin adresini bulur ve gerektiğinde verileri sıralayarak bağımsız değişkenlerini yığına iter.  
  
    > [!NOTE]
    > DLL'nin bulunması ve yüklenmesi ve bellekteki işlevin adresinin bulunması yalnızca işlevin ilk çağrısında gerçekleşir.  
  
4. Denetimi yönetilmeyen işleve aktarın.  
  
 Platform çağırma, yönetilen arayaniçin yönetilmeyen işlev tarafından oluşturulan özel durumlar atar.

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kod ile Birlikte Çalışma](index.md)
- [Platform Çağırma Örnekleri](platform-invoke-examples.md)
- [Birlikte Çalışma Hazırlama](interop-marshaling.md)
