---
title: ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb41cc47351ccf22fcd522b7d4291c235312bfaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167695"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
Etkinleştirir veya sanal modül bölme devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `enableSplitting`  
 `true` Sanal modül bölme etkinleştirmek için; `false` devre dışı.  
  
## <a name="remarks"></a>Açıklamalar  
 Neden bölme sanal Modülü [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) birlikte derleme sırasında birleştirilen modülleri işlemek ve onları bir grup tek büyük bir modül yerine ayrı bir modül olarak sunmak tanımak için. Bunun yapılması, çeşitli davranışını değiştirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemleri aşağıda açıklanmıştır.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
 Bu yöntem çağrılabilir ve değerini `enableSplitting` herhangi bir zamanda değiştirilebilir. Durum bilgisi olan işlevsel değişiklikler neden olmaz bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) listelenen yöntemleri davranışını değiştirme dışındaki nesne [modülü sanal bölme ve yönetilmeyen hata ayıklama API'leri](#APIs) Bölüm zaman çağrılır. Sanal modüllerini kullanarak bu yöntemleri çağrılırken bir performans cezasına sebep. Ayrıca, önemli bellek içi sanallaştırılmış meta verilerini önbelleğe doğru uygulamak için gerekli olabilecek [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) bile sanal modül bölme kapatıldı sonra API'leri ve bu önbellekler korunmayabilir.  
  
## <a name="terminology"></a>Terminoloji  
 Sanal modül bölme açıklayan aşağıdaki terimler kullanılır:  
  
 kapsayıcı modülleri veya kapsayıcıları  
 Toplama modülleri.  
  
 alt modülleri veya sanal modülleri  
 Kapsayıcıda bulunan modüller.  
  
 Normal modülleri  
 Modül oluşturma zamanında birleştirilmiş değil. Kapsayıcı modülleri ne alt modülleri değildirler.  
  
 Kapsayıcı modülleri hem alt modülleri Icordebugmodule arabirimi nesneleri tarafından temsil edilir. Ancak, arabirim davranışını her durumda, biraz daha farklı olarak \<x-başvuru bölümüne > bölümde açıklanmaktadır.  
  
## <a name="modules-and-assemblies"></a>Modül ve derlemelerdeki  
 Bir modül ve derleme arasında bire bir ilişki olduğundan senaryoları, birleştirme derlemesi için birden çok modül derlemeleri desteklenmez. Kapsayıcı modülü veya bir alt modül olup olmadığını gösteren bağımsız olarak her Icordebugmodule nesnesi, karşılık gelen Icordebugassembly nesne sahiptir. [Icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) yöntemi derlemeye modülünden dönüştürür. Diğer yönde eşlemek için [Icordebugassembly::enumeratemodules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) yöntemi yalnızca 1 modülü numaralandırır. Assembly ve module sıkı eşleşmiş bir çift bu durumda oluşturduğundan koşulları assembly ve module büyük ölçüde değiştirilebilir hale gelir.  
  
## <a name="behavioral-differences"></a>Davranışsal farklılıklar  
 Kapsayıcı modüller aşağıdaki davranışları ve özelliklere sahiptir:  
  
-   Tüm bağlı alt modüller için meta verilerinin birlikte birleştirilir.  
  
-   Tür adlarının karıştırılmış.  
  
-   [Icordebugmodule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) yöntemi bir diskteki modülüne yolunu döndürür.  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) yöntemi, o yansıma boyutunu döndürür.  
  
-   Alt modülleri ICorDebugAssembly3.EnumerateContainedAssemblies yöntemi listeler.  
  
-   ICorDebugAssembly3.GetContainerAssembly yöntemi döndürür `S_FALSE`.  
  
 Alt modüller aşağıdaki davranışları ve özelliklere sahiptir:  
  
-   Birleştirilmiş yalnızca özgün derlemeye karşılık gelen meta verileri sınırlı bir dizi sahiptirler.  
  
-   Meta veri adlarının karıştırılmış değil.  
  
-   Meta veri belirteçleri oluşturma işleminde birleştirilmesinden önce orijinal derleme belirteçlerinde eşleşecek şekilde düşüktür.  
  
-   [Icordebugmodule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) yöntemi, derleme adı, dosya yolu döndürür.  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) yöntemi özgün birleştirilmemiş resim boyutu döndürür.  
  
-   ICorDebugModule3.EnumerateContainedAssemblies yöntemi döndürür `S_FALSE`.  
  
-   İçeren modül ICorDebugAssembly3.GetContainerAssembly yöntemi döndürür.  
  
## <a name="interfaces-retrieved-from-modules"></a>Modüllerden alınan arabirimler  
 Arabirimleri çeşitli oluşturulabilir veya modüllerden alınır. Bunlardan bazıları:  
  
-   Tarafından döndürülen Icordebugclass nesneyi [Icordebugmodule::getclassfromtoken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) yöntemi.  
  
-   Tarafından döndürülen Icordebugassembly nesneyi [Icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) yöntemi.  
  
 Bu nesneler tarafından her zaman önbelleğe alınan [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), ve mi oluşturulmuş veya kapsayıcı modülü ya da bir alt modül sorgulanan bağımsız olarak aynı işaretçi kimliğe sahip olur. Alt modül filtrelenmiş bir görünüm değil ayrı bir önbellekle kendi kopya bu önbelleğe alınan nesneleri sağlar.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Sanal modül bölme ve yönetilmeyen hata ayıklama API'leri  
 Aşağıdaki tabloda, yönetilmeyen hata ayıklama API'SİNDE diğer yöntemleri davranışını etkiler bölme nasıl sanal modülü gösterir.  
  
|Yöntem|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::getmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Bu işlevin ilk olarak tanımlanan alt modül döndürür|Bu işlev uygulamasına birleştirildiği container modül döndürür|  
|[Icordebugclass::getmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Bu sınıf ilk olarak tanımlanan alt modül döndürür.|Bu sınıf, içine birleştirildiği container modül döndürür.|  
|ICorDebugModuleDebugEvent::GetModule|Yüklenen kapsayıcı modülü döndürür. Alt modülleri yükleme olaylarının bu ayardan bağımsız olarak sunulmaz.|Yüklenen kapsayıcı modülü döndürür.|  
|[Icordebugappdomain::enumerateassemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Alt derlemeleri ve normal derlemelerin bir listesini döndürür; hiçbir kapsayıcı derlemeyi dahil edilir. **Not:**  Herhangi bir kapsayıcı derleme simgeleri eksik, kendi alt derlemeleri hiçbiri numaralandırılır. Herhangi bir normal derleme simgeleri eksik, olabilir veya numaralandırılmış değil.|Kapsayıcı derlemeleri ve normal derlemelerin bir listesini döndürür; hiçbir alt derlemeyi dahil edilir. **Not:**  Herhangi bir normal derleme simgeleri eksik, olabilir veya numaralandırılmış değil.|  
|[Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (yalnızca IL kodu söz konusu olduğunda)|Derleme öncesi birleştirme görüntüde geçerli olabilecek IL döndürür. Özellikle, başvurulan türleri IL içeren sanal modülde tanımlı değil, herhangi bir satır içi meta veri belirteçleri TypeRef veya MemberRef belirteçleri doğru olur. İçinde bu TypeRef veya MemberRef belirteçleri aranabilir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) karşılık gelen sanal Icordebugmodule nesne için nesne.|IL sonrası birleştirme derleme görüntüyü döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
