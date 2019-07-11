---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes yöntemi
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaecbe3640e5da78c13a077611887c6b62d355a4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771521"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::GetAssemblyImageBytes yöntemi
Birleştirilmiş derlemeye göreli sanal adres (RVA) verilen birleştirilmiş bir bütünleştirilmiş koddan verileri okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `rva`  
 [in] Birleştirilmiş bir derlemeye göreli sanal adres (RVA).  
  
 `length`  
 Birleştirilmiş derlemeden okunacak bayt sayısı.  
  
 `ppMemoryBuffer`  
 Adresine bir işaretçi bir [Icordebugmemorybuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) bellek arabelleği ile birleştirilmiş derleme meta verileri hakkında bilgi içeren nesne.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
