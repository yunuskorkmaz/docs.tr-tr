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
ms.openlocfilehash: fbf6ce8c8c9628b08872058a794fb0e005764ab1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501306"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod Yöntemi
Belirtilen imzaya sahip bir yöntem veya genel işlev için tanım oluşturur ve bu yöntem tanımına bir belirteç döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `mdTypedef`Metodun üst sınıfının veya üst arabiriminin belirteci. `td` `mdTokenNil` Genel bir işlev tanımlıyorsanız, olarak ayarlayın.  
  
 `szName`  
 'ndaki Unicode 'daki üye adı.  
  
 `dwMethodFlags`  
 'ndaki Metodun veya genel işlevin özniteliklerini belirten [Cormethodadttr](cormethodattr-enumeration.md) numaralandırması değeri.  
  
 `pvSigBlob`  
 'ndaki Yöntem imzası. İmza, belirtilen şekilde kalıcı hale getirilir. Herhangi bir parametre için ek bilgi belirtmeniz gerekiyorsa, [ımetadatayayma:: SetParamProps](imetadataemit-setparamprops-method.md) metodunu kullanın.  
  
 `cbSigBlob`  
 'ndaki İçindeki bayt sayısı `pvSigBlob` .  
  
 `ulCodeRVA`  
 'ndaki Kodun adresi.  
  
 `dwImplFlags`  
 'ndaki Metodun uygulama özelliklerini belirten [CorMethodImpl](cormethodimpl-enumeration.md) numaralandırması değeri.  
  
 `pmd`  
 dışı Üye belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veri API 'SI, bu yöntemleri, bu parametre içinde belirtilen bir kapsayan sınıf veya arabirim için arayanla aynı sırada kalıcı hale getirme garantisi verir `td` .  
  
 `DefineMethod`Ve belirli parametre ayarlarının kullanımıyla ilgili ek bilgiler aşağıda verilmiştir.  
  
## <a name="slots-in-the-v-table"></a>V tablosundaki yuvalar  
 Çalışma zamanı, v tablosu yuvaları ayarlamak için yöntem tanımlarını kullanır. Bir veya daha fazla yuvanın bir COM arabirim düzeniyle eşlik koruması olması gibi bir veya daha fazla yuva atlanması gerektiği durumlarda, v tablosundaki yuva veya yuvaları almak için bir kukla Yöntem tanımlanmıştır; öğesini `dwMethodFlags` `mdRTSpecialName` [Cormethodadttr](cormethodattr-enumeration.md) numaralandırmasının değerine ayarlayın ve adı şu şekilde belirtin:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 Burada *SequenceNumber* , yöntemin dizi numarasıdır ve *Countofslotlar* , v tablosundaki atlanacak yuva sayısıdır. *Countofslotlar* atlanırsa, 1 varsayılır. Bu kukla Yöntemler yönetilen veya yönetilmeyen koddan çağrılabilir değildir ve bunları, yönetilen veya yönetilmeyen koddan çağırma girişimleri bir özel durum oluşturur. Tek amacı, çalışma zamanının COM tümleştirmesi için oluşturduğu v tablosunda yer kaplamesidir.  
  
## <a name="duplicate-methods"></a>Yinelenen Yöntemler  
 Yinelenen yöntemleri tanımlamamalısınız. Diğer bir deyişle,, `DefineMethod` ve parametrelerinde yinelenen bir değer kümesiyle çağırmamalıdır `td` `wzName` `pvSig` . (Bu üç parametre birlikte, yöntemini benzersiz bir şekilde tanımlar.). Ancak, yöntem tanımlarından biri için `mdPrivateScope` parametreyi parametre içinde ayarlayabilmeniz için yinelenen bir üçlü kullanabilirsiniz `dwMethodFlags` . ( `mdPrivateScope` Bit, derleyicinin bu yöntem tanımına bir başvuru yaymayacağı anlamına gelir.)  
  
## <a name="method-implementation-information"></a>Yöntem uygulama bilgileri  
 Yöntem uygulamasıyla ilgili bilgiler genellikle yöntemin bildirildiği sırada bilinmez. Bu nedenle, `ulCodeRVA` çağırma sırasında ve parametrelerinde değerleri geçirmeniz gerekmez `dwImplFlags` `DefineMethod` . Değerler, daha sonra [ımetadatayayma:: SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) veya [ımetadatayayma:: SetRVA](imetadataemit-setrva-method.md)aracılığıyla uygun şekilde sağlanabilir.  
  
 Platform çağrısı (PInvoke) veya COM birlikte çalışma senaryoları gibi bazı durumlarda, Yöntem gövdesi sağlanmaz ve `ulCodeRVA` sıfıra ayarlanmalıdır. Bu durumlarda, çalışma zamanı uygulamayı bulacağından yöntem soyut olarak etiketlenmemelidir.  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke için bir yöntem tanımlama  
 Her yönetilmeyen işlevin PInvoke aracılığıyla çağrılması için, hedef yönetilmeyen işlevi temsil eden bir yönetilen yöntem tanımlamanız gerekir. Yönetilen yöntemi tanımlamak için, `DefineMethod` PInvoke 'un kullanıldığı yönteme bağlı olarak belirli değerlere ayarlanmış parametrelerden bazıları ile kullanın:  
  
- Doğru PInvoke-yönetilmeyen bir DLL 'de bulunan harici bir yönetilmeyen yöntemin çağrılmasını içerir.  
  
- Yerel PInvoke-geçerli yönetilen modüle eklenmiş yerel bir yönetilmeyen yöntemin çağrılmasını içerir.  
  
 Parametre ayarları aşağıdaki tabloda verilmiştir.  
  
|Parametre|Doğru PInvoke için değerler|Yerel PInvoke için değerler|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Ayarla `mdStatic` ; clear `mdSynchronized` ve `mdAbstract` .|  
|`pvSigBlob`|Geçerli yönetilen türler içeren parametrelere sahip geçerli bir ortak dil çalışma zamanı (CLR) yöntemi imzası.|Geçerli yönetilen türler içeren parametrelere sahip geçerli bir CLR yöntemi imzası.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|`miCil`Ve ayarlayın `miManaged` .|`miNative`Ve ayarlayın `miUnmanaged` .|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
