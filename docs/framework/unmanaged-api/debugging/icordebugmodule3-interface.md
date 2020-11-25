---
title: ICorDebugModule3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 543a1a3c79b6cf3eb799da5844f35286dfa91940
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709563"
---
# <a name="icordebugmodule3-interface"></a>ICorDebugModule3 Arabirimi

Dinamik modül için simge okuyucu oluşturur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi](icordebugmodule3-createreaderforinmemorysymbols-method.md)|Dinamik bir modül için bir sembol okuyucu (genellikle [ıstreamunmanagedreader arabirimi](../diagnostics/isymunmanagedreader-interface.md)) oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu arabirim "ICorDebugModule" ve "ICorDebugModule2" arabirimlerini mantıksal olarak genişletir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 4,5, 4, 3,5 SP1
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemoteTarget Arabirimi](icordebugremotetarget-interface.md)
- [ICorDebug Arabirimi](icordebug-interface.md)

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
