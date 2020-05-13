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
ms.openlocfilehash: 5bcced647af6436bd8f5b1f3779d9368b6173d11
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213042"
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
 [out] `true` `pPotentialParentFrame`Geçerli çerçevenin üst öğesi ise, tersi durumda `false` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Üst durum başarıyla döndürüldü.|  
|E_FAIL|Üst durum döndürülemedi.|  
|E_INVALIDARG|`pPotentialParentFrame`ya da `pIsParent` null.|  
  
## <a name="exceptions"></a>Özel durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 `IsMatchingParentFrame``true`yöntemine geçirdiğiniz çerçeve nesnesinin, yöntemin çağrıldığı çerçeve nesnesinin üst öğesi olup olmadığını döndürür. Yöntemi belirtilen çerçevenin alt öğesi olmayan bir çerçevede çağırırsanız, bir hata döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugNativeFrame2 Arabirimi](icordebugnativeframe2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
