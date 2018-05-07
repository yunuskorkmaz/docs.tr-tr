---
title: ICorDebugModule2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a56b5c31c26dbe5c5371fdb7a10c13ad11847117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus Yöntemi
Bu Icordebugmodule2 belirtilen değerle hariç tüm sınıfların tüm yöntemleri yalnızca My kod (JMC) durumunu ayarlar `pTokens` ters değerine ayarlar dizi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bIsJustMycode`  
 [in] Kümesine `true` kod hata ayıklaması; tersi durumda ise, kümesine `false`.  
  
 `cTokens`  
 [in] Boyutunu `pTokens` dizi.  
  
 `pTokens`  
 [in] Bir dizi `mdToken` değerleri, her biri başvurduğu JMC durumunu kümesine sahip bir yöntem!`bIsJustMycode`.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen her yöntemi JMC durumunu `pTokens` dizi karşıtı için ayarlanmış `bIsJustMycode` değeri. Bu modüldeki tüm diğer yöntemleri durumunu ayarlamak `bIsJustMycode` değeri.  
  
 `SetJMCStatus` Yöntemi bu modüldeki tüm önceki JMC ayarlarını siler.  
  
 `SetJMCStatus` Yöntemi hatalı döndürürse S_OK HRESULT tüm işlevleri başarıyla ayarlandı. CORDBG_E_FUNCTION_NOT_DEBUGGABLE bazı çalışırsa, HRESULT işaretlenir döndürür `true` debuggable değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
