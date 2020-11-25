---
title: 'Icordebugmergedassemblyrecord:: GetVersion yöntemi'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 7352a77fc8f41124d7e6c78a3dfc6ccd6d3a94aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710512"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>Icordebugmergedassemblyrecord:: GetVersion yöntemi

Derlemenin sürüm bilgilerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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

 Derleme sürüm numaraları hakkında bilgi için bkz <xref:System.Version> . sınıf konusu.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMergedAssemblyRecord Arabirimi](icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
