---
title: 'Icordebugmergedassemblyrecord:: GetVersion yöntemi'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 8b5995183be7f1c992cf3230e16456cb248eff0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793076"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>Icordebugmergedassemblyrecord:: GetVersion yöntemi
Derlemenin sürüm bilgilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pMajor`  
 dışı Ana sürüm numarasına yönelik bir işaretçi.  
  
 `pMinor`  
 dışı Küçük sürüm numarasına yönelik bir işaretçi.  
  
 `pBuild`  
 dışı Yapı numarasına yönelik bir işaretçi.  
  
 `pRevision`  
 dışı Düzeltme numarasına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme sürüm numaraları hakkında daha fazla bilgi için <xref:System.Version> sınıfı konusuna bakın.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMergedAssemblyRecord Arabirimi](icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
