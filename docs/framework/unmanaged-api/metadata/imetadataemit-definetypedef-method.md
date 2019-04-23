---
title: IMetaDataEmit::DefineTypeDef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b6f5881f289bed258191baf4f43264ea6ba35db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141810"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef Yöntemi
Ortak dil çalışma zamanı tür için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szTypeDef`  
 [in] Unicode türünün adı.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` öznitelikleri. Bu, bir bit maskesi, `CoreTypeAttr` değerleri.  
  
 `tkExtends`  
 [in] Belirteç temel sınıf. Aşağıdakilerden biri olması gereken bir `mdTypeDef` veya `mdTypeRef` belirteci.  
  
 `rtkImplements`  
 [in] Bu sınıf veya arabirim uyguladığı arabirimlerin belirtme belirteçleri dizisi.  
  
 `ptd`  
 [out] `mdTypeDef` Atanan simgesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Eklenen bir bayrak `dwTypeDefFlags` oluşturulan türü bir ortak tür sistemi başvuru türü (sınıfı veya arabirimi) ya da bir ortak tür sistemi değer türü olup olmadığını belirtir.  
  
 Belirtilen parametreler bağlı olarak, bu yöntem bir yan etkisi da oluşturabilir bir `mdInterfaceImpl` devralınan veya bu tür tarafından uygulanan her arabirim için kayıt. Ancak, bu yöntem bunlardan birine döndürmeyen `mdInterfaceImpl` belirteçleri. Daha sonra eklemek veya değiştirmek bir istemci istiyorsa, bir `mdInterfaceImpl` belirteci, bunu kullanmalı `IMetaDataImport` bunları numaralandırmak için arabirim. COM semantikleri kullanmak istiyorsanız `[default]` arabirimi, sağladığınız varsayılan arabirimi ilk öğesi olarak `rtkImplements`; sınıfın varsayılan bir arabirim vardır sınıfına özel bir öznitelik belirtir (hangi olduğu her zaman varsayılır İlk `mdInterfaceImpl` belirteci bildirilen sınıf için).  
  
 Her öğeyi `rtkImplements` dizi içeren bir `mdTypeDef` veya `mdTypeRef` belirteci. Dizi içerisindeki son öğe olmalıdır `mdTokenNil`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
