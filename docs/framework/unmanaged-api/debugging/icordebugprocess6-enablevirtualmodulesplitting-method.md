---
title: ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 8ad15d11ce81323b30434b3db98259a74a198f29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178565"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
Sanal modülün bölünmesini sağlar veya devre dışı kılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `enableSplitting`  
 `true`sanal modülün bölünmesini etkinleştirmek için; `false` devre dışı kılabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Sanal modül bölme [işlemi, ICorDebug'un](icordebug-interface.md) yapı işlemi sırasında birleştirilmiş modülleri tanımasına ve bunları tek bir büyük modül yerine ayrı modüller grubu olarak sunmasını neden eder. Bunu yapmak, aşağıda açıklanan çeşitli [ICorDebug](icordebug-interface.md) yöntemlerinin davranışını değiştirir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
 Bu yöntem çağrılabilir ve `enableSplitting` değeri herhangi bir zamanda değiştirilebilir. Sanal modül bölmede listelenen yöntemlerin davranışını ve çağrıldıkları anda [yönetilmeyen hata ayıklama API'leri](#APIs) bölümünü değiştirmek dışında, bir [ICorDebug](icordebug-interface.md) nesnesinde durumsal işlevsel değişikliklere neden olmaz. Sanal modüllerin kullanılması, bu yöntemleri ararken bir performans cezasına neden olur. Buna ek olarak, sanallaştırılmış meta verilerin önemli bellek önbelleğe alınması [iMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) API'lerini doğru bir şekilde uygulamak için gerekli olabilir ve sanal modül bölme söndükten sonra bile bu önbellekler tutulabilir.  
  
## <a name="terminology"></a>Terminoloji  
 Sanal modül bölme yi tanımlarken aşağıdaki terimler kullanılır:  
  
 konteyner modülleri veya konteynerler  
 Agrega modülleri.  
  
 alt modüller veya sanal modüller  
 Bir kapta bulunan modüller.  
  
 düzenli modüller  
 Oluşturma zamanında birleştirilemeyen modüller. Bunlar ne konteyner modülleri ne de alt modülleridir.  
  
 Hem konteyner modülleri hem de alt modülleri ICorDebugModule arabirim nesneleri ile temsil edilir. Ancak, \<x-ref bölüm> bölümünde açıklandığı gibi, arabirimin davranışı her durumda biraz farklıdır.  
  
## <a name="modules-and-assemblies"></a>Modüller ve montajlar  
 Çok modüllü derlemeler derleme birleştirme senaryoları için desteklenmez, bu nedenle modül ve derleme arasında bire bir ilişki vardır. Her ICorDebugModule nesnesi, bir kapsayıcı modülveya bir alt modülü temsil edip etmediğine bakılmaksızın, karşılık gelen bir ICorDebugAssembly nesnesi vardır. [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) yöntemi modülden montaja dönüşür. Diğer yönde haritalamak için, [ICorDebugAssembly::Sayısal Modüller](icordebugassembly-enumeratemodules-method.md) yöntemi yalnızca 1 modül numarası verir. Montaj ve modül bu durumda sıkıca birleştirilmiş bir çift oluşturduğundan, montaj ve modül terimleri büyük ölçüde değiştirilebilir hale gelir.  
  
## <a name="behavioral-differences"></a>Davranış farklılıkları  
 Konteyner modülleri aşağıdaki davranış ve özelliklere sahiptir:  
  
- Tüm kurucu alt modüller için meta verileri birleştirilir.  
  
- Tür adları ezilmiş olabilir.  
  
- [ICorDebugModule::GetName](icordebugmodule-getname-method.md) yöntemi yolu bir disk modülüne döndürür.  
  
- [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) yöntemi bu görüntünün boyutunu döndürür.  
  
- ICorDebugAssembly3.EnumerateContainedAssemblies yöntemi alt modülleri listeler.  
  
- ICorDebugAssembly3.GetContainerAssembly yöntemi `S_FALSE`döndürür.  
  
 Alt modüller aşağıdaki davranış ve özelliklere sahiptir:  
  
- Yalnızca birleştirilen özgün derlemeye karşılık gelen azaltılmış bir meta veri kümeleri vardır.  
  
- Meta veri adları ezilmiş değildir.  
  
- Meta veri belirteçlerinin, yapı işleminde birleştirilmeden önce orijinal derlemedeki belirteçlerle eşleşmesi olası değildir.  
  
- [ICorDebugModule::GetName](icordebugmodule-getname-method.md) yöntemi bir dosya yolu değil, derleme adını döndürür.  
  
- [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) yöntemi orijinal birleştirilmiş görüntü boyutunu döndürür.  
  
- ICorDebugModule3.EnumerateContainedAssemblies yöntemi `S_FALSE`döndürür.  
  
- ICorDebugAssembly3.GetContainerAssembly yöntemi içeren modülü döndürür.  
  
## <a name="interfaces-retrieved-from-modules"></a>Modüllerden alınan arabirimler  
 Modüllerden çeşitli arabirimler oluşturulabilir veya alınabilir. Bunlardan bazıları:  
  
- [ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) yöntemi ile döndürülen bir ICorDebugClass nesnesi.  
  
- [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) yöntemi ile döndürülen bir ICorDebugAssembly nesnesi.  
  
 Bu nesneler her zaman [ICorDebug](icordebug-interface.md)tarafından önbelleğe alınır ve kapsayıcı modülünden veya alt modülden oluşturulup oluşturulmadığına bakılmaksızın aynı işaretçi kimliğine sahip olurlar. Alt modül, kendi kopyaları ile ayrı bir önbellek değil, bu önbelleğe alınmış nesnelerin filtrelenmiş bir görünüm sağlar.  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Sanal modül bölme ve yönetilmeyen hata ayıklama API'leri  
 Aşağıdaki tablo, sanal modül bölmenin yönetilmeyen hata ayıklama API'sındaki diğer yöntemlerin davranışını nasıl etkilediğini gösterir.  
  
|Yöntem|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|Bu işlevin başlangıçta tanımlandığı alt modülü döndürür|Bu işlevin birleştiği kapsayıcı modülünü döndürür|  
|[ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|Bu sınıfın başlangıçta tanımlandığı alt modülü döndürür.|Bu sınıfın birleştiği kapsayıcı modülünü döndürür.|  
|ICorDebugModuleDebugOlay::GetModule|Yüklenen konteyner modüllerini döndürür. Alt modüllere bu ayara bakılmaksızın yük olayları verilmez.|Yüklenen konteyner modüllerini döndürür.|  
|[ICorDebugAppDomain::Sayısal Montajlar](icordebugappdomain-enumerateassemblies-method.md)|Alt derlemelerin ve düzenli derlemelerin listesini verir; konteyner derlemeleri dahil değildir. **Not:**  Herhangi bir kapsayıcı derlemesi sembolleri eksikse, alt derlemelerinin hiçbiri numaralandırılmayacak. Herhangi bir normal montaj sembolleri eksikse, numaralandırılabilir veya numaralandırılmayabilir.|Konteyner derlemelerinin ve düzenli montajların listesini verir; alt derlemeler dahil değildir. **Not:**  Herhangi bir normal montaj sembolleri eksikse, numaralandırılabilir veya numaralandırılmayabilir.|  
|[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (yalnızca IL koduna atıfta bulunulurken)|Birleştirme öncesi derleme görüntüsünde geçerli olacak IL'yi döndürür. Özellikle, atıfta bulunulan türler IL içeren sanal modülde tanımlanmadığında, satır içinde herhangi bir meta veri belirteçleri doğru bir şekilde TypeRef veya MemberRef belirteçleri olacaktır. Bu TypeRef veya MemberRef belirteçleri, ilgili sanal ICorDebugModule nesnesi için [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) nesnesinde aranabilir.|Birleştirme sonrası derleme görüntüsünde IL'yi döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
