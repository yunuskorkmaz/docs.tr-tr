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
ms.openlocfilehash: 0e54027806cef07fad4740c3bf5226fd26c72570
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108771"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum İşlevi
Derlemedeki nesneleri belirtilen [IAssemblyName](iassemblyname-interface.md)ile numaralandıracak bir [IAssemblyEnum](iassemblyenum-interface.md) örneğine yönelik bir işaretçi alır.  
  
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
 dışı İstenen `IAssemblyEnum` işaretçisini içeren bir bellek konumu işaretçisi.  
  
 `pUnkReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pUnkReserved`, null bir başvuru olmalıdır.  
  
 `pName`  
 'ndaki İstenen derlemenin `IAssemblyName`. Bu ad, numaralandırmayı filtrelemek için kullanılır. Genel derleme önbelleğindeki tüm derlemeleri listelemek için null olabilir.  
  
 `dwFlags`  
 'ndaki Numaralandırıcının davranışını değiştirme bayrakları. Bu parametre [asm_cache_flags](asm-cache-flags-enumeration.md) numaralandırmasından tam olarak bir bit içerir.  
  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved`, null bir başvuru olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwFlags` parametresi `ASM_CACHE_FLAGS` numaralandırmasından tam olarak bir bit içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyEnum Arabirimi](iassemblyenum-interface.md)
- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
