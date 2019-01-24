---
title: ICorDebugVariableSymbol::GetSlotIndex yöntemi
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09b50af49f8379539773d2000a6c1f8222fee875
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563840"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>ICorDebugVariableSymbol::GetSlotIndex yöntemi
Yerel bir değişken yönetilen yuvası dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pSlotIndex`  
 [out] Yerel değişkenin yuvası dizini için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` başarılı olursa. `E_FAIL` değişken, işlev bağımsız değişkeni ise.  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel bir değişken yönetilen yuvası dizinini değişkenin meta veri bilgilerini almak için kullanılabilir  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugVariableSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
