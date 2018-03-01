---
title: "IMetaDataEmit::DefineMethod Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fa136f5e6669e58ef709db5b53f538804cfcac2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod Yöntemi
Belirtilen imzayla yöntemi veya genel işlevi için bir tanım oluşturur ve bu yöntem tanımı için bir belirteç döndürür.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] `mdTypedef` Üst sınıf veya yöntemin üst arabirimi belirteci. Ayarlama `td` için `mdTokenNil`, genel bir işlev tanımlıyorsanız.  
  
 `szName`  
 [in] Unicode üye adı.  
  
 `dwMethodFlags`  
 [in] Değerini [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) yöntemi veya genel işlev özniteliklerini belirtir numaralandırması.  
  
 `pvSigBlob`  
 [in] Yöntem imzası. İmza verdiği kalıcıdır. Ek bilgi için herhangi bir parametre belirtmeniz gerekiyorsa, kullanın [Imetadataemit::setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) yöntemi.  
  
 `cbSigBlob`  
 [in] Bayt sayısı `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] Kod adresi.  
  
 `dwImplFlags`  
 [in] Değerini [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) yöntemi uygulama özelliklerini belirten numaralandırma.  
  
 `pmd`  
 [out] Üye belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Arayan bunları verilen kapsayan sınıf veya belirtilen arabirimi için gösterdiği gibi yöntemleri aynı sırayla kalıcı hale getirmek API meta verileri garanti `td` parametresi.  
  
 Kullanımı ile ilgili ek bilgiler `DefineMethod` ve belirli parametre ayarları aşağıda verilmiştir.  
  
## <a name="slots-in-the-v-table"></a>V tablosundaki yuvaları  
 Çalışma zamanı yöntemi tanımları v tablo yuvaları ayarlamak için kullanır. Burada bir veya daha fazla yuvaları Atlanan, bu tür gerekecektir durumda bir COM arabirimi Düzen eşlikli korumak için bir kukla yöntemi yuvası ya da v tablosundaki yuvası kaplayan için tanımlanmış bir; ayarlama `dwMethodFlags` için `mdRTSpecialName` değerini [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırma ve farklı bir ad belirtin:  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>  
  
 Burada *SequenceNumber* yöntemi sıra sayısı ve *CountOfSlots* v tabloda atlamak için yuva sayısı. Varsa *CountOfSlots* olan atlanırsa, 1 varsayılır. Bu kukla yöntemleri yönetilen veya yönetilmeyen koddan aranabilir değildir ve bunları yönetilen veya yönetilmeyen koddan çağırma girişimi herhangi bir özel durum oluşturur. COM tümleştirme için çalışma zamanı oluşturur v tablo yer yalnızca amaçlarına gerçekleşir.  
  
## <a name="duplicate-methods"></a>Yinelenen yöntemleri  
 Yinelenen yöntemleri tanımlamamalıdır. Diğer bir deyişle, değil çağırmalısınız `DefineMethod` yinelenen değerler kümesiyle `td`, `wzName`, ve `pvSig` parametreleri. (Şu üç parametreyi birlikte benzersiz olarak yöntemi tanımlayın.). Ancak, yöntem tanımlarını biri için ayarladığınız olması koşuluyla, yinelenen Üçlü kullanabilirsiniz `mdPrivateScope` içinde bit `dwMethodFlags` parametresi. ( `mdPrivateScope` Bit anlamına gelir derleyici bu yöntem tanımını başvuru yayma değil.)  
  
## <a name="method-implementation-information"></a>Yöntemi uygulama bilgileri  
 Yöntem uygulaması hakkında bilgi yöntemi bildirilmiş aynı anda bilinmiyor genellikle. Bu nedenle, değerleri geçirmek gerekmez `ulCodeRVA` ve `dwImplFlags` çağrılırken parametreleri `DefineMethod`. Değerleri daha sonra aracılığıyla sağlanabilir [Imetadataemit::setmethodımplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) veya [Imetadataemit::setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)uygun şekilde.  
  
 Platform çağırma (PInvoke) veya COM birlikte çalışma senaryoları gibi bazı durumlarda, yöntem gövdesi sunulacaktır değil, ve `ulCodeRVA` sıfır olarak ayarlanması gerekir. Çalışma zamanı uygulama bulur çünkü bu gibi durumlarda yöntemi soyut olarak etiketlenmesi gerektiğine değil.  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke için bir yöntem tanımlama  
 Yönetilmeyen her işlev PInvoke aracılığıyla çağrılacak bilgi için yönetilmeyen hedef işlevi temsil eden bir yönetilen yöntemi tanımlamanız gerekir. Yönetilen yöntemi tanımlamak için `DefineMethod` bazı PInvoke kullanılır şekilde bağlı olarak belirli değerler için ayarlanan parametreler:  
  
-   TRUE PInvoke - yönetilmeyen DLL içinde bulunduğu bir dış yönetilmeyen yöntemi çağrıldı içerir.  
  
-   Yerel PInvoke - geçerli yönetilen modül katıştırılmış yerel bir yönetilmeyen yöntemi çağrıldı içerir.  
  
 Parametre ayarları aşağıdaki tabloda verilmiştir.  
  
|Parametre|Doğru PInvoke değerleri|Yerel PInvoke değerleri|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Ayarlama `mdStatic`; clear `mdSynchronized` ve `mdAbstract`.|  
|`pvSigBlob`|Yönetilen türler geçerli bir ortak dil çalışma zamanı (CLR) yöntemi imzası geçerli parametrelere sahip.|Yönetilen türler geçerli parametrelere sahip geçerli bir CLR yöntemi imzası.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Ayarlama `miCil` ve `miManaged`.|Ayarlama `miNative` ve `miUnmanaged`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
