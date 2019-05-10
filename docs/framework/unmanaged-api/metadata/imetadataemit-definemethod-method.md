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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4879af90aa06515a95b4d15f039ff3c2b1a88f62
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665021"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod Yöntemi
Belirtilen imzayla bir yöntem veya genel bir işlev için bir tanım oluşturur ve bu yöntem tanımını bir belirteç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] `mdTypedef` Üst sınıf veya yöntemin üst arabirimi belirteci. Ayarlama `td` için `mdTokenNil`, genel bir işlev tanımlıyorsanız.  
  
 `szName`  
 [in] Üye adı Unicode.  
  
 `dwMethodFlags`  
 [in] Değerini [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) yöntemi veya genel işlev özniteliklerini belirten sabit listesi.  
  
 `pvSigBlob`  
 [in] Yöntem imzası. İmza sağlanan olarak kalıcı hale getirilir. Daha fazla bilgi için herhangi bir parametre belirtmeniz gerekiyorsa, kullanın [Imetadataemit::setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) yöntemi.  
  
 `cbSigBlob`  
 [in] Bayt sayısı `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] Kod adresi.  
  
 `dwImplFlags`  
 [in] Değerini [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) yöntemi uygulama özelliklerinin belirten sabit listesi.  
  
 `pmd`  
 [out] Üye belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bunları yayan çağıranın verilen kapsayan sınıfı veya arabirimi, belirtilen gibi yöntemleri aynı sırayla kalıcı hale getirmek meta veri API'si garanti `td` parametresi.  
  
 Kullanımı ile ilgili ek bilgiler `DefineMethod` ve belirli parametre ayarlarını aşağıda verilmiştir.  
  
## <a name="slots-in-the-v-table"></a>V-table yuvaları  
 Çalışma zamanı yöntemi tanımları v-table yuvaları ayarlamak için kullanır. Bir veya daha fazla yuva Atlanan, böyle olması için gereken yere durumda, yuva veya v-table yuvalarda yararlanmak için işlevsiz bir yöntem eşlikli bir COM arabirimi düzeni korumak için farklı tanımlanır; ayarlama `dwMethodFlags` için `mdRTSpecialName` değerini [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) sabit listesi adı olarak belirtin:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 Burada *SequenceNumber* yöntemi sıra sayısı ve *CountOfSlots* v tablosunda atlamak için yuvaları sayısıdır. Varsa *CountOfSlots* olan atlanırsa, 1 varsayılır. İşlevsiz bu yöntemler yönetilen veya yönetilmeyen koddan çağrılabilir değildir ve her türlü girişim, yönetilen veya yönetilmeyen koddan çağırmak için bir özel durum oluşturur. V-table için COM tümleştirme çalışma zamanının oluşturduğu alan yalnızca amaçlarına gerçekleşir.  
  
## <a name="duplicate-methods"></a>Yinelenen yöntemleri  
 Yinelenen yöntemleri tanımlanmamalıdır. Diğer bir deyişle, değil, çağırmalıdır `DefineMethod` yinelenen değerleri kümesi ile `td`, `wzName`, ve `pvSig` parametreleri. (Şu üç parametreyi birlikte yöntem benzersiz olarak tanımlayın.). Ancak, yöntem tanımlarını biri için ayarladığınız olması koşuluyla, yinelenen bir Üçlü kullanabilirsiniz `mdPrivateScope` içindeki bit `dwMethodFlags` parametresi. ( `mdPrivateScope` Bit Derleyici bu yöntem tanımını başvuru yayma değil demektir.)  
  
## <a name="method-implementation-information"></a>Uygulama bilgileri yöntemi  
 Yöntem uygulaması hakkında bilgi yöntemi bildirilen zamanında bilinen değildir. Bu nedenle, değerleri geçirmek gerekmez `ulCodeRVA` ve `dwImplFlags` çağırırken parametre `DefineMethod`. Değerleri daha sonra aracılığıyla sağlanabilir [Imetadataemit::setmethodımplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) veya [Imetadataemit::setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)uygun şekilde.  
  
 Platform çağırma (PInvoke) veya COM birlikte çalışma senaryoları gibi bazı durumlarda, yöntem gövdesini sunulacaktır değil, ve `ulCodeRVA` sıfır olarak ayarlayın. Çalışma zamanı uygulaması çünkü bu gibi durumlarda yöntemi soyut olarak etiketlenmesi değil.  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke için bir yöntem tanımlama  
 PInvoke aracılığıyla çağrılan her yönetilmeyen bir işlev için hedef yönetilmeyen işlev temsil eden bir yönetilen yöntemin tanımlamanız gerekir. Yönetilen yöntemi tanımlamak için `DefineMethod` bazı parametreler PInvoke kullanıldığı şekilde bağlı olarak belirli değerlere ayarlayın:  
  
- PInvoke true - yönetilmeyen DLL içinde yer alan bir dış yönetilmeyen yöntemi çağırmayı içerir.  
  
- Yerel PInvoke - geçerli yönetilen modülde gömülü yerel bir yönetilmeyen yöntemini çağırmayı içerir.  
  
 Parametre ayarları aşağıdaki tabloda verilmiştir.  
  
|Parametre|Değerleri için doğru PInvoke|Yerel PInvoke değerleri|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Ayarlama `mdStatic`; clear `mdSynchronized` ve `mdAbstract`.|  
|`pvSigBlob`|Yönetilen türler geçersiz parametrelerle geçerli ortak dil çalışma zamanı (CLR) metodu imzası.|Yönetilen türler geçersiz parametrelerle geçerli bir CLR metodu imzası.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Ayarlama `miCil` ve `miManaged`.|Ayarlama `miNative` ve `miUnmanaged`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
