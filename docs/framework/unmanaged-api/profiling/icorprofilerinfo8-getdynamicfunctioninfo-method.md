---
title: 'ICorProfilerInfo8:: Getdynamicfunctionınfo'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 90246ade67f797c04f0da5d9a68dadb83e4ce418
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973707"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi
  
 Dinamik yöntemler hakkında bilgi alır.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Bilgi alınacak işlevin KIMLIĞI.  

 `moduleId`  
 'ndaki İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.  
  
 `ppvSig`  
 dışı İşlev için imzaya yönelik bir işaretçi.  
  
 `pbSig`  
 dışı İşlev imzası için bayt sayısına yönelik bir işaretçi.
  
 `cchName`  
 'ndaki `wszName` Dizinin en büyük boyutu.
  
 `pcchName`  
 dışı `wszName` Dizideki karakterlerin sayısı.

 `wszName` \
 dışı Bir dizi `WCHAR` , varsa işlevin adıdır.
  
## <a name="remarks"></a>Açıklamalar  
 Il saplamaları veya LCG gibi bazı yöntemlerin [IMetaDataImport](../metadata/imetadataimport-interface.md) ve [IMetaDataImport2](../metadata/imetadataimport2-interface.md) API 'leri kullanılarak alınabilecek ilişkili meta verileri yoktur. Bu tür yöntemlere profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)dinleyerek erişilebilir.

 Bu API, varsa kolay bir ad dahil dinamik yöntemler hakkında bilgi almak için kullanılabilir.  
  

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [! [NET_CURRENT_V472PLUS](../../../../includes/net-current-v472plus.md) Ekle  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo8 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

