---
description: ': Imetadatayayma::D efineTypeDef yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: ca0c74b8c067771e9f45a8c00639d75c9ad08de1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784047"
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
 [in] `TypeDef` özelliklerine. Bu bir değer bit değeridir `CoreTypeAttr` .  
  
 `tkExtends`  
 'ndaki Taban sınıfının belirteci. `mdTypeDef`Ya da bir `mdTypeRef` belirteç olmalıdır.  
  
 `rtkImplements`  
 'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.  
  
 `ptd`  
 dışı `mdTypeDef` Atanan belirteç.  
  
## <a name="remarks"></a>Açıklamalar  

 İçindeki bayrak `dwTypeDefFlags` , oluşturulan türün ortak bir tür sistem başvuru türü (sınıf veya arabirim) mi yoksa ortak bir tür sistemi değer türü mi olduğunu belirtir.  
  
 Sağlanan parametrelere bağlı olarak, bu yöntem yan bir efekt olarak `mdInterfaceImpl` Bu tür tarafından devralınan veya uygulanan her arabirim için bir kayıt da oluşturabilir. Ancak, bu yöntem bu belirteçlerden herhangi birini döndürmez `mdInterfaceImpl` . Bir istemci daha sonra bir belirteç eklemek veya bir belirteci değiştirmek isterse `mdInterfaceImpl` , `IMetaDataImport` bunları numaralandırmak için arabirimini kullanması gerekir. Arabirimin COM semantiğini kullanmak istiyorsanız `[default]` , varsayılan arabirimi ' de ilk öğe olarak sağlamalısınız `rtkImplements` ; sınıfta ayarlanan özel bir öznitelik, sınıfın varsayılan bir arabirime sahip olduğunu belirtir (Bu, her zaman `mdInterfaceImpl` sınıf için belirtilen ilk belirteç olduğunu varsayacaktır).  
  
 Dizideki her öğe `rtkImplements` bir `mdTypeDef` veya `mdTypeRef` belirtecini barındırır. Dizideki son öğe olmalıdır `mdTokenNil` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
