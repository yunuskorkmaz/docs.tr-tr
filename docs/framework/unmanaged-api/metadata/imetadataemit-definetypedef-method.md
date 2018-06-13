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
ms.openlocfilehash: 54691785e3b2619b5f4a2eecc510800b4b5cee07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446603"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef Yöntemi
Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `szTypeDef`  
 [in] Unicode türünün adı.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` öznitelikleri. Bu, bir bit maskesi olan `CoreTypeAttr` değerleri.  
  
 `tkExtends`  
 [in] Belirtecin temel sınıf. Aşağıdakilerden biri olması gereken bir `mdTypeDef` veya bir `mdTypeRef` belirteci.  
  
 `rtkImplements`  
 [in] Bu sınıf veya arabirimi uygulayan arabirimlerini belirtme belirteçleri dizisi.  
  
 `ptd`  
 [out] `mdTypeDef` Atanan simgesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bayrak `dwTypeDefFlags` oluşturulan türü bir ortak sistem başvuru türü (sınıf veya arabirim) veya ortak bir sistem değer türü olup olmadığını belirtir.  
  
 Belirtilen parametreler bağlı olarak, bu yöntem bir yan etkisi da oluşturabilir bir `mdInterfaceImpl` devralınan veya bu türü tarafından uygulanan her bir arabirim için kayıt. Ancak, bu yöntem herhangi birini döndürmez `mdInterfaceImpl` belirteçleri. Daha sonra eklemek veya değiştirmek bir istemci istiyorsa, bir `mdInterfaceImpl` belirteç, bunu kullanmalı `IMetaDataImport` bunları numaralandırmak için arabirim. COM semantiği kullanmak istiyorsanız, `[default]` arabirimi, sağladığınız varsayılan arabirimi ilk öğe olarak `rtkImplements`; set sınıfı üzerinde özel bir öznitelik sınıfı varsayılan arabirimi olduğunu gösterir (hangi olduğu her zaman varsayılır İlk `mdInterfaceImpl` belirteci bildirilen sınıfı için).  
  
 Her öğeye `rtkImplements` dizi ayrı tutma bir `mdTypeDef` veya `mdTypeRef` belirteci. Dizi son öğesi olmalı `mdTokenNil`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
