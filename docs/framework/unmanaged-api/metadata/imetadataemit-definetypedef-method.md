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
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450221"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef Yöntemi
Ortak dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Unicode 'daki türün adı.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` öznitelikleri. Bu, `CoreTypeAttr` değerlerinin bir bit dır.  
  
 `tkExtends`  
 'ndaki Taban sınıfının belirteci. `mdTypeDef` ya da `mdTypeRef` belirteci olmalıdır.  
  
 `rtkImplements`  
 'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.  
  
 `ptd`  
 dışı `mdTypeDef` belirteci atandı.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwTypeDefFlags` bir bayrak, oluşturulan türün ortak bir tür sistem başvuru türü (sınıf veya arabirim) mi yoksa ortak bir tür sistemi değer türü mi olduğunu belirtir.  
  
 Sağlanan parametrelere bağlı olarak, bu yöntem bir yan etkisi olarak, bu tür tarafından devralınan veya uygulanan her arabirim için bir `mdInterfaceImpl` kaydı da oluşturabilir. Ancak, bu yöntem bu `mdInterfaceImpl` belirteçlerinin hiçbirini döndürmez. Bir istemci daha sonra bir `mdInterfaceImpl` belirtecini eklemek veya değiştirmek isterse, bunları numaralandırmak için `IMetaDataImport` arabirimini kullanması gerekir. `[default]` arabiriminin COM semantiğini kullanmak istiyorsanız, varsayılan arabirimi `rtkImplements`ilk öğe olarak sağlamalısınız; sınıfında ayarlanan özel bir öznitelik, sınıfın varsayılan bir arabirime sahip olduğunu gösterir (Bu, her zaman sınıf için bildirildiği ilk `mdInterfaceImpl` belirteç olarak varsayılır).  
  
 `rtkImplements` dizisinin her öğesi bir `mdTypeDef` veya `mdTypeRef` belirteci barındırır. Dizideki son öğe `mdTokenNil`olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
