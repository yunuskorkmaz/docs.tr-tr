---
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 032f32a08efa92cea682b0e2fc974dc607a9dca4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133947"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppAssemblies`  
 dışı Numaralandırıcı olan ICorDebugAssemblyEnum arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu `ICorDebugAssembly3` nesne bir kapsayıcı ise `S_OK`; Aksi takdirde, `S_FALSE`ve numaralandırma boştur.  
  
## <a name="remarks"></a>Açıklamalar  
 İçerilen derlemeleri listelemek için semboller gereklidir. Yoksa, yöntem `S_FALSE`döndürür ve geçerli numaralandırıcı sağlanmaz.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugAssembly3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
