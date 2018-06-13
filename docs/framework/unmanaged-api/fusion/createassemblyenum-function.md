---
title: CreateAssemblyEnum İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2098d5d9ce1c01f232cf2904c1fd3e990dfbe2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432122"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum İşlevi
Bir işaretçi alır bir [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) Belirtilen derlemedeki nesneleri listeleme örneği [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pEnum`  
 [out] İstenen içeren bir bellek konumunu işaretçi `IAssemblyEnum` işaretçi.  
  
 `pUnkReserved`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `pUnkReserved` bir null başvuru olması gerekir.  
  
 `pName`  
 [in] `IAssemblyName` İstenen derlemenin. Bu ad numaralandırma filtrelemek için kullanılır. Tüm derlemeleri genel derleme önbelleğinde Numaralandırılacak null olabilir.  
  
 `dwFlags`  
 [in] Numaralandırıcının davranışını değiştirmek için işaretler. Bu parametre tam olarak bir bit içerir [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) numaralandırması.  
  
 `pvReserved`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `pvReserved` bir null başvuru olması gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwFlags` Parametre içeren tam olarak bir bit `ASM_CACHE_FLAGS` numaralandırması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [IAssemblyName Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
