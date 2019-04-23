---
title: ICorDebugSymbolProvider::GetCodeRange yöntemi
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52fd0e9dac1d255197909d153099d9c6f2bd8ff7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212940"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a>ICorDebugSymbolProvider::GetCodeRange yöntemi
Yöntemi başlangıç adresi ve bir yöntemde göreli sanal adres (RVA) verilen boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `codeRva`  
 [in] Bir yöntem in göreli sanal adres (RVA).  
  
 `pCodeStartAddress`  
 [out] Yöntemi başlangıç adresi için bir işaretçi.  
  
 `pCodeSize`  
 Yöntemi kod boyutu (yöntemin koduna bayt sayısı) için bir işaretçi.  
  
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
