---
title: ICorDebugMergedAssemblyRecord::GetVersion yöntemi
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36cf8647b3caafeaae2db3c2fd53471496e922fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666953"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergedAssemblyRecord::GetVersion yöntemi
Derlemenin sürüm bilgilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pMajor`  
 [out] Ana sürüm numarası bir işaretçi.  
  
 `pMinor`  
 [out] Alt sürüm numarasını bir işaretçi.  
  
 `pBuild`  
 [out] Yapı numarası bir işaretçi.  
  
 `pRevision`  
 [out] Düzeltme numarası için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme sürüm numaraları hakkında daha fazla bilgi için bkz: <xref:System.Version> sınıf konusuna.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMergedAssemblyRecord Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
