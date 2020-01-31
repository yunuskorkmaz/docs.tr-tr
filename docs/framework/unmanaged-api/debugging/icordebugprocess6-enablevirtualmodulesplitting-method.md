---
title: ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 224acc9ed61bc2753a5e763dd2c3d4af63300d64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792253"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting Yöntemi
Sanal modül bölmeyi etkinleştirilir veya devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `enableSplitting`  
 sanal modül bölünmesini etkinleştirmek için `true`; devre dışı bırakmak için `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Sanal modül bölünmesi, [ICorDebug](icordebug-interface.md) 'ın derleme işlemi sırasında birlikte birleştirilmiş modülleri tanımasını ve bunları tek bir büyük modül yerine ayrı modüller grubu olarak sunmasını sağlar. Bunun yapılması, aşağıda açıklanan çeşitli [ICorDebug](icordebug-interface.md) yöntemlerinin davranışını değiştirir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
 Bu yöntem çağrılabilir ve `enableSplitting` değeri herhangi bir zamanda değiştirilebilir. Bir [ICorDebug](icordebug-interface.md) nesnesinde durum bilgisi olan herhangi bir işlev değişikliğine neden olmaz, bu, [sanal modül bölme ve yönetilmeyen hata ayıklama API 'leri](#APIs) bölümünde listelenen yöntemlerin davranışını değiştirdikleri sırada değiştirmemiştir. Sanal modüllerin kullanılması, bu yöntemler çağrılırken bir performans cezası uygular. Ayrıca, [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) API 'lerinin doğru bir şekilde uygulanması için sanallaştırılan önemli bellek içi önbelleğe alma gerekebilir ve sanal modül bölünmesi devre dışı bırakılsa bile bu önbellekler korunabilir.  
  
## <a name="terminology"></a>Terminoloji  
 Sanal modül bölünmesi açıklanırken aşağıdaki terimler kullanılır:  
  
 kapsayıcı modülleri veya kapsayıcılar  
 Toplama modülleri.  
  
 alt modüller veya sanal modüller  
 Kapsayıcıda bulunan modüller.  
  
 normal modüller  
 Derleme zamanında birleştirilmeyen modüller. Bunlar kapsayıcı modülleri veya alt modüller değildir.  
  
 Hem kapsayıcı modülleri hem de alt modüller ICorDebugModule arabirim nesneleriyle temsil edilir. Ancak, \<x-ref ' i Bölüm > bölümünde açıklanan şekilde, arabirimin davranışı her durumda biraz farklıdır.  
  
## <a name="modules-and-assemblies"></a>Modüller ve derlemeler  
 Birden çok modüllü derlemeler derleme birleştirme senaryolarında desteklenmez, bu nedenle bir modül ve derleme arasında bire bir ilişki vardır. Her ICorDebugModule nesnesi, bir kapsayıcı modülünü mi yoksa bir alt modülün mi temsil ettiğini bağımsız olarak karşılık gelen bir ICorDebugAssembly nesnesine sahiptir. [ICorDebugModule:: GetAssembly](icordebugmodule-getassembly-method.md) yöntemi modülünden derlemeye dönüştürür. Diğer yönde eşlemek için [ICorDebugAssembly:: EnumerateModules](icordebugassembly-enumeratemodules-method.md) yöntemi yalnızca 1 modül numaralandırır. Derleme ve modül bu durumda sıkı bir şekilde bağlanmış bir çift biçimli olduğundan, hüküm derlemesi ve modülü büyük ölçüde değiştirilebilir hale gelir.  
  
## <a name="behavioral-differences"></a>Davranış farkları  
 Kapsayıcı modülleri aşağıdaki davranış ve özelliklere sahiptir:  
  
- Tüm bileşen alt modüllerinin meta verileri birlikte birleştirilir.  
  
- Tür adları karışmış olabilir.  
  
- [ICorDebugModule:: GetName](icordebugmodule-getname-method.md) yöntemi, disk üzerindeki bir modülün yolunu döndürür.  
  
- [ICorDebugModule:: GetSize](icordebugmodule-getsize-method.md) yöntemi bu görüntünün boyutunu döndürür.  
  
- ICorDebugAssembly3. EnumerateContainedAssemblies yöntemi alt modülleri listeler.  
  
- ICorDebugAssembly3. GetContainerAssembly metodu `S_FALSE`döndürür.  
  
 Alt modüller aşağıdaki davranış ve özelliklere sahiptir:  
  
- Yalnızca birleştirilen özgün derlemeye karşılık gelen azaltılmış meta veri kümesine sahiptirler.  
  
- Meta veri adları karışmış değil.  
  
- Meta veri belirteçleri, derleme sürecinde birleştirilmeden önce özgün derlemedeki belirteçlerle eşleşmek düşüktür.  
  
- [ICorDebugModule:: GetName](icordebugmodule-getname-method.md) metodu, bir dosya yolu değil, derleme adını döndürür.  
  
- [ICorDebugModule:: GetSize](icordebugmodule-getsize-method.md) yöntemi orijinal birleştirilmemiş görüntünün boyutunu döndürür.  
  
- ICorDebugModule3. EnumerateContainedAssemblies yöntemi `S_FALSE`döndürür.  
  
- ICorDebugAssembly3. GetContainerAssembly yöntemi kapsayan modülü döndürür.  
  
## <a name="interfaces-retrieved-from-modules"></a>Modüllerden alınan arabirimler  
 Modüllerden çeşitli arabirimler oluşturulabilir veya alınalınabilir. Bunlardan bazıları:  
  
- [ICorDebugModule:: GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) yöntemi tarafından döndürülen bir ICorDebugClass nesnesi.  
  
- [ICorDebugModule:: GetAssembly](icordebugmodule-getassembly-method.md) yöntemi tarafından döndürülen bir ICorDebugAssembly nesnesi.  
  
 Bu nesneler her zaman [ICorDebug](icordebug-interface.md)tarafından önbelleğe alınır ve kapsayıcı modülünden veya bir alt modülden oluşturulup sorgulanmadığına bakılmaksızın aynı işaretçi kimliğine sahip olur. Alt modül, bu önbelleğe alınmış nesnelerin filtrelenmiş bir görünümünü sağlar, kendi kopyaları olan ayrı bir önbellek değildir.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Sanal modül bölme ve yönetilmeyen hata ayıklama API 'Leri  
 Aşağıdaki tabloda, sanal modül ayırmanın yönetilmeyen hata ayıklama API 'sindeki diğer yöntemlerin davranışını nasıl etkilediği gösterilmektedir.  
  
|Yöntem|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction:: GetModule](icordebugfunction-getmodule-method.md)|Bu işlevin ilk olarak tanımlandığı alt modülü döndürür|Bu işlevin birleştirildiği kapsayıcı modülünü döndürür|  
|[ICorDebugClass:: GetModule](icordebugclass-getmodule-method.md)|Bu sınıfın başlangıçta tanımlandığı alt modülü döndürür.|Bu sınıfın birleştirildiği kapsayıcı modülünü döndürür.|  
|Icordebugmoduledebugger gevent:: GetModule|Yüklenen kapsayıcı modülünü döndürür. Bu ayardan bağımsız olarak alt modüllere, yük olayları verilmez.|Yüklenen kapsayıcı modülünü döndürür.|  
|[ICorDebugAppDomain:: EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|Alt derlemelerin ve normal derlemelerin bir listesini döndürür; kapsayıcı derlemeleri dahil değildir. **Note:**  Herhangi bir kapsayıcı derlemesinde sembol yoksa, alt derlemelerin hiçbiri NUMARALANDIRILAMAZ. Herhangi bir normal derlemede sembol eksikse, bu, numaralandırılabilir veya Numaralandırılmayabilir.|Kapsayıcı derlemelerinin ve normal derlemelerin bir listesini döndürür; hiçbir alt derleme dahil değildir. **Note:**  Herhangi bir normal derlemede sembol eksikse, bu, numaralandırılabilir veya Numaralandırılmayabilir.|  
|[ICorDebugCode:: GetCode](icordebugcode-getcode-method.md) (yalnızca Il koduna başvuru yaparken)|Bir birleştirme öncesi derleme görüntüsünde geçerli olacak Il 'yi döndürür. Özellikle, başvuruda bulunulan türler Il 'yi içeren sanal modülde tanımlanmadığında, satır içi meta veri belirteçleri doğru şekilde TypeRef veya MemberRef belirteçleri olacaktır. Bu TypeRef veya MemberRef belirteçleri, karşılık gelen sanal ICorDebugModule nesnesi için [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) nesnesinde aranabilir.|Birleştirme sonrası derleme görüntüsündeki Il 'yi döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
