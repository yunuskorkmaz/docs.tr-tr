---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6faf8960c06488c8fff5a076aae375529e1d0260
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138865"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a>ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi
Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cRequestedRecords`  
 'ndaki İstenen sembol kaydı sayısı.  
  
 `pcFetchedRecords`  
 dışı Yöntemi tarafından alınan sembol kayıtlarının sayısına yönelik bir işaretçi.  
  
 `pRecords`  
 [Icordebugmergedassemblyrecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) nesnelerinin dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
