---
title: IMetaDataEmit::DefineMethod Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177676"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod Yöntemi
Belirtilen imzaile bir yöntem veya global işlev için bir tanım oluşturur ve bu yöntem tanımına bir belirteç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [içinde] Yöntemin `mdTypedef` üst sınıf veya üst arabiriminin belirteci. `td` Genel `mdTokenNil`bir işlev tanımlıyorsanız,  
  
 `szName`  
 [içinde] Unicode'daki üye adı.  
  
 `dwMethodFlags`  
 [içinde] Yöntemin veya genel işlevin özniteliklerini belirten [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırmasının değeri.  
  
 `pvSigBlob`  
 [içinde] Yöntem imzası. İmza verilen şekilde devam etti. Herhangi bir parametre için ek bilgi belirtmeniz gerekiyorsa, [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) yöntemini kullanın.  
  
 `cbSigBlob`  
 [içinde] Bayt `pvSigBlob`sayısı.  
  
 `ulCodeRVA`  
 [içinde] Kodun adresi.  
  
 `dwImplFlags`  
 [içinde] Yöntemin uygulama özelliklerini belirten [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) numaralandırmadeğeri.  
  
 `pmd`  
 [çıkış] Üye belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veri API' si, yöntemleri arayanın `td` parametrede belirtilen belirli bir çevreleyen sınıf veya arabirim için yayıdığı sırada devam etmesini garanti eder.  
  
 Kullanımı `DefineMethod` ve belirli parametre ayarları ile ilgili ek bilgiler aşağıda verilmiştir.  
  
## <a name="slots-in-the-v-table"></a>V tablosundaki yuvalar  
 Çalışma zamanı, v-table yuvalarını ayarlamak için yöntem tanımlarını kullanır. Com arabirim düzeniyle pariteyi korumak gibi bir veya daha fazla yuvanın atlanmaları gerektiğinde, v-tablosundaki yuva veya yuvaları almak için sahte bir yöntem tanımlanır; CorMethodAttr numaralandırma değerini ayarlayın ve adını şu şekilde belirtin: [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) `dwMethodFlags` `mdRTSpecialName`  
  
 _VtblGap\<*DizisiSayı*>\<\_*Sayısı*>
  
 *SequenceNumber* yöntemin sıra numarası ve *CountOfSlots* v-tablosunda atlamak için yuva sayısıdır. *CountOfSlots* atlanırsa, 1 kabul edilir. Bu sahte yöntemler yönetilen veya yönetilmeyen koddan çağrılabilir değildir ve yönetilen veya yönetilmeyen koddan bunları çağırma girişimi bir özel durum oluşturur. Tek amaçları, çalışma zamanının COM tümleştirmesi için oluşturduğu v tablosunda yer açmaktır.  
  
## <a name="duplicate-methods"></a>Yinelenen Yöntemler  
 Yinelenen yöntemleri tanımlamamalısınız. Diğer bir deyişle, `DefineMethod` `td`, ve `wzName` `pvSig` parametreleri değerleri yinelenen bir dizi ile aramamalısınız. (Bu üç parametre birlikte benzersiz yöntemi tanımlar.). Ancak, yöntem tanımlarından biri için `mdPrivateScope` `dwMethodFlags` parametredeki biti ayarlamanız koşuluyla yinelenen üçlü kullanabilirsiniz. (Bit, `mdPrivateScope` derleyicinin bu yöntem tanımına bir başvuru yayılmayacağı anlamına gelir.)  
  
## <a name="method-implementation-information"></a>Yöntem Uygulama Bilgileri  
 Yöntem in ekinde yöntem uygulaması hakkında bilgiler genellikle bilinmemektedir. Bu nedenle, ararken `ulCodeRVA` `dwImplFlags` `DefineMethod`değerleri ve parametreleri geçmek gerekmez. Değerler daha sonra [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) veya [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), uygun şekilde sağlanabilir.  
  
 Platform çağırma (PInvoke) veya COM interop senaryoları gibi bazı durumlarda, yöntem gövdesi `ulCodeRVA` sağlanmaz ve sıfıra ayarlanmalıdır. Çalışma zamanı uygulamayı bulacağı için, bu gibi durumlarda yöntem soyut olarak etiketlenmemiştir.  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke için Bir Yöntem Tanımlama  
 Yönetilmeyen her işlevin PInvoke aracılığıyla çağrılabilmesi için, hedef yönetilmeyen işlevi temsil eden yönetilen bir yöntem tanımlamanız gerekir. Yönetilen yöntemi tanımlamak için, PInvoke'in nasıl kullanıldığına bağlı olarak belirli değerlere ayarlanmış bazı parametreleri kullanın: `DefineMethod`  
  
- True PInvoke - yönetilmeyen bir DLL'de bulunan harici yönetilmeyen bir yöntemin çağrılması içerir.  
  
- Yerel PInvoke - geçerli yönetilen modüle katıştırılmış yerel bir yönetilmeyen yöntem invocation içerir.  
  
 Parametre ayarları aşağıdaki tabloda verilmiştir.  
  
|Parametre|Gerçek PInvoke değerleri|Yerel PInvoke değerleri|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Set `mdStatic`; açık `mdSynchronized` `mdAbstract`ve .|  
|`pvSigBlob`|Geçerli yönetilen türleri parametreleri ile geçerli bir ortak dil çalışma zamanı (CLR) yöntemi imza.|Geçerli yönetilen türleri parametreleri ile geçerli bir CLR yöntemi imza.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Ayarlayın `miCil` `miManaged`ve .|Ayarlayın `miNative` `miUnmanaged`ve .|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
