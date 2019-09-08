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
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795378"
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
 dışı İstenen `IAssemblyEnum` işaretçiyi içeren bir bellek konumu işaretçisi.  
  
 `pUnkReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pUnkReserved`null bir başvuru olmalıdır.  
  
 `pName`  
 'ndaki `IAssemblyName` İstenen derlemenin ' i. Bu ad, numaralandırmayı filtrelemek için kullanılır. Genel derleme önbelleğindeki tüm derlemeleri listelemek için null olabilir.  
  
 `dwFlags`  
 'ndaki Numaralandırıcının davranışını değiştirme bayrakları. Bu parametre [asm_cache_flags](asm-cache-flags-enumeration.md) numaralandırmasından tam olarak bir bit içerir.  
  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved`null bir başvuru olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwFlags` Parametresi `ASM_CACHE_FLAGS` Numaralandırmadaki tam olarak bir bit içeriyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyEnum Arabirimi](iassemblyenum-interface.md)
- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
