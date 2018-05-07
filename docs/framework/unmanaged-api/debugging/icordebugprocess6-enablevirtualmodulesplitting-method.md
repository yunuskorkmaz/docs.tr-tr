---
title: ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4565deddee2e7714d937bf61574243cc07a4602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
Etkinleştirir veya sanal modülü bölme devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `enableSplitting`  
 `true` Sanal modülü bölme etkinleştirmek için; `false` devre dışı bırakmak için.  
  
## <a name="remarks"></a>Açıklamalar  
 Nedenler bölme sanal Modülü [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) derleme sırasında birlikte birleştirilen modülleri işlemek ve bunları tek bir büyük modül yerine ayrı modülleri bir grup olarak sunmak tanımak için. Bunun yapılması, çeşitli davranışını değiştirir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemleri aşağıda açıklanmıştır.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
 Bu yöntem çağrılır ve değerini `enableSplitting` herhangi bir zamanda değiştirilebilir. Durum bilgisi olan işlevsel değişiklikler neden olmaz bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) listelenen yöntemleri davranışını değiştiren dışında nesne [sanal modülü bölme ve yönetilmeyen hata ayıklama API'leri](#APIs) zamana bölüm. Sanal modüllerini kullanma performans cezasına bu yöntemleri çağrılırken sebep. Ayrıca, önemli bellek içi sanallaştırılmış meta verileri önbelleğe doğru uygulama için gerekli olabilecek [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) bile sanal modülü bölme kapatıldı sonra API'ları ve bu önbellekler korunmayabilir.  
  
## <a name="terminology"></a>Terminoloji  
 Aşağıdaki terimler sanal modülü bölme tanımlarken kullanılır:  
  
 kapsayıcı modülleri veya kapsayıcıları  
 Birleşik modüller.  
  
 alt modülleri ya da sanal modülleri  
 Bir kapsayıcıda bulunan modüller.  
  
 Normal modülleri  
 Derleme zamanında birleştirilen değil modüller. Kapsayıcı modülleri ne alt modülleri oldukları.  
  
 Kapsayıcı modülleri ve alt modülleri Icordebugmodule arabirimi nesneleri ile temsil edilir. Ancak, arabirim davranışını her durumda, biraz farklıdır olarak \<x-ref bölümüne > bölümünde açıklanmaktadır.  
  
## <a name="modules-and-assemblies"></a>Modülleri ve derlemeler  
 Derleme; böylece bir modül ve derleme arasında bire bir ilişki senaryoları, birleştirme için çok modülü derlemeleri desteklenmez. Onu bir kapsayıcı modül veya bir alt modül gösteren bağımsız olarak her Icordebugmodule nesnenin karşılık gelen bir Icordebugassembly nesnesini vardır. [Icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) yöntemi derlemeye modülünden dönüştürür. Diğer yönü eşlemek için [Icordebugassembly::enumeratemodules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) yöntemi yalnızca 1 modülü numaralandırır. Derleme ve modülü sıkı şekilde bağlı çifti bu durumda form olduğundan, modül ve şartları derleme büyük ölçüde değiştirilebilir haline gelir.  
  
## <a name="behavioral-differences"></a>Davranış farklılıkları  
 Kapsayıcı modülleri aşağıdaki davranışları ve özelliklere sahiptir:  
  
-   Tüm bağlı alt modülleri için kendi meta verileri birlikte birleştirilir.  
  
-   Tür adları karıştırılmış.  
  
-   [Icordebugmodule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) yöntemi bir disk üzerinde modülü yolunu döndürür.  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) yöntemi, görüntü boyutu döndürür.  
  
-   ICorDebugAssembly3.EnumerateContainedAssemblies yöntemi alt modüllerini listeler.  
  
-   ICorDebugAssembly3.GetContainerAssembly yöntemi döndürür `S_FALSE`.  
  
 Alt modülleri aşağıdaki davranışları ve özelliklere sahiptir:  
  
-   Azaltılmış birleştirildiği yalnızca özgün derleme için karşılık gelen meta verileri sahiptirler.  
  
-   Meta veri adlarının karıştırılmış değil.  
  
-   Meta veri simgesi yapı işleminde birleştirildiği önce özgün derleme belirteçlerinde eşleşecek şekilde düşüktür.  
  
-   [Icordebugmodule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) yöntemi derleme adı, dosya yolunu döndürür.  
  
-   [Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) yöntemi özgün birleştirilmemiş resim boyutu döndürür.  
  
-   ICorDebugModule3.EnumerateContainedAssemblies yöntemi döndürür `S_FALSE`.  
  
-   ICorDebugAssembly3.GetContainerAssembly yöntemi içeren modülü döndürür.  
  
## <a name="interfaces-retrieved-from-modules"></a>Modüllerden alınan arabirimleri  
 Arabirimleri çeşitli oluşturulan veya modüllerden alınamıyor. Bunlardan bazıları şunlardır:  
  
-   Tarafından döndürülen Icordebugclass nesneyi [Icordebugmodule::getclassfromtoken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) yöntemi.  
  
-   Tarafından döndürülen Icordebugassembly nesneyi [Icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) yöntemi.  
  
 Bu nesneler her zaman tarafından önbelleğe alınan [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), ve olup oluşturulmuş veya kapsayıcısına modül ya da bir alt modülünden sorgulanan bakılmaksızın aynı işaretçi kimliğe sahip. Filtre uygulanmış bir görünüm değil ayrı bir önbelleği kendi kopyalarla bu önbelleğe alınan nesnelerin alt modülü sağlar.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Sanal modülü bölme ve hata ayıklama yönetilmeyen API'ler  
 Aşağıdaki tabloda, yönetilmeyen hata ayıklama API'si diğer yöntemleri davranışını etkiler bölme nasıl sanal modülü gösterir.  
  
|Yöntem|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::getmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Bu işlev ilk olarak tanımlanan alt modül döndürür|Bu işlev içine birleştirildiği kapsayıcısına modül döndürür|  
|[Icordebugclass::getmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Bu sınıf ilk olarak tanımlanan alt modül döndürür.|Bu sınıf içine birleştirildiği kapsayıcısına modül döndürür.|  
|ICorDebugModuleDebugEvent::GetModule|Yüklenen kapsayıcısına modül döndürür. Bu ayardan bağımsız olarak yük olayları alt modülleri verilmedi.|Yüklenen kapsayıcısına modül döndürür.|  
|[Icordebugappdomain::enumerateassemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Alt derlemeler ve normal derleme listesini döndürür; kapsayıcı derlemeleri dahil edilir. **Not:** herhangi bir kapsayıcı derlemesinin simge eksikse, kendi alt derlemeleri hiçbiri numaralandırılır. Normal bir derleme simge eksikse olabilir veya numaralandırılmış değil.|Kapsayıcı derlemeler ve normal derleme listesini döndürür; hiçbir alt derlemeleri dahil edilir. **Not:** normal derlemeler simge eksikse olabilir veya numaralandırılmış değil.|  
|[Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (IL kodu için söz konusu olduğunda)|Bir ön birleştirme derleme görüntüsündeki geçerliliğini yitirir IL döndürür. Özellikle, başvurulan türleri IL içeren sanal modülünde tanımlı değil, tüm satır içi meta veri simgesi TypeRef veya MemberRef belirteçleri doğru olur. İçinde bu TypeRef veya MemberRef belirteçleri aranabilir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) karşılık gelen sanal Icordebugmodule nesnesi için nesnesi.|IL sonrası birleştirme derleme görüntüde döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
