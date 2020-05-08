---
title: ICorDebugDataTarget3::GetLoadedModules Yöntemi
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: c3565f4f9284bc121b0e2d3b0885cbea927acfdd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976427"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>ICorDebugDataTarget3::GetLoadedModules Yöntemi
Şimdiye kadar yüklenmiş modüllerin listesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cRequestedModules`  
 'ndaki Bilgilerin istendiği modül sayısı.  
  
 `pcFetchedModules`  
 dışı Bilgilerin döndürüldüğü modül sayısına yönelik bir işaretçi.  
  
 `pLoadedModules`  
 dışı Yüklü modüller hakkında bilgi sağlayan [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) nesneleri dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget3 Arabirimi](icordebugdatatarget3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
