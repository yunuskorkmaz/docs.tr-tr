---
title: "ICorDebugModule2::SetJMCStatus Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a461a9c05b18de45426247743c6e4ffca775025a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
