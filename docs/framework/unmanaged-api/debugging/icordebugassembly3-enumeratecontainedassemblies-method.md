---
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 616675f839e562227558ece440bdfdf497747572
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784570"
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

- [ICorDebugAssembly3 Arabirimi](icordebugassembly3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
