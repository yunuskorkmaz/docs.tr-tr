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
ms.openlocfilehash: c56b0168df6e4aee69b5d3e5fbbe027ca2c8974a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778448"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum İşlevi
Bir işaretçi alır bir [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) nesneleri ile belirtilen derlemedeki numaralandırabilirsiniz örneği [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametreler  
 `pEnum`  
 [out] İstenen içeren bir bellek konumuna işaretçi `IAssemblyEnum` işaretçi.  
  
 `pUnkReserved`  
 [in] Sonra genişletilebilmek için ayrılmış. `pUnkReserved` null bir başvuru olmalıdır.  
  
 `pName`  
 [in] `IAssemblyName` İstenen derleme. Bu ad, numaralandırma filtrelemek için kullanılır. Genel derleme önbelleğini tüm derlemeleri numaralandırmak için null olabilir.  
  
 `dwFlags`  
 [in] Numaralandırıcının davranışını değiştirmek için kullanılan bayraklar. Bu parametre içeren tam bir bit [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) sabit listesi.  
  
 `pvReserved`  
 [in] Sonra genişletilebilmek için ayrılmış. `pvReserved` null bir başvuru olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwFlags` Parametre içeren tam bir bit `ASM_CACHE_FLAGS` sabit listesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [IAssemblyName Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
