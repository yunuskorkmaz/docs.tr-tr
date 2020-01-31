---
title: ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: aeaa706ef35413a728f8b254cd325f0bcc83acd1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792707"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>ICorDebugNativeFrame2::IsMatchingParentFrame Yöntemi
Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pPotentialParentFrame`  
 'ndaki Üst durum için değerlendirmek istediğiniz çerçeve nesnesine yönelik bir işaretçi.  
  
 `pIsParent`  
 [out] `pPotentialParentFrame` geçerli çerçevenin üst öğesi ise `true`; Aksi takdirde, `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Üst durum başarıyla döndürüldü.|  
|E_FAIL|Üst durum döndürülemedi.|  
|E_INVALIDARG|`pPotentialParentFrame` veya `pIsParent` null.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 `IsMatchingParentFrame`, yöntemine geçirdiğiniz çerçeve nesnesinin, yöntemin çağrıldığı üst öğesi ise `true` döndürür. Yöntemi belirtilen çerçevenin alt öğesi olmayan bir çerçevede çağırırsanız, bir hata döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugNativeFrame2 Arabirimi](icordebugnativeframe2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
