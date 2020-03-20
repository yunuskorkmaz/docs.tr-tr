---
title: ICorDebugAppDomain::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179085"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName Yöntemi
Uygulama etki alanının adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchName`  
 [içinde] `szName` Dizinin boyutu. Bu yöntemi sorgu moduna koymak için bu değeri sıfıra ayarlayın.  
  
 `pcchName`  
 [çıkış] Adın boyutuna veya gerçekte döndürülen `szName`karakter sayısına işaretçi. Sorgu modunda, bu değer arayan ada ne kadar büyük bir arabellek ayırmak için bildirin.  
  
 `szName`  
 [çıkış] Uygulama etki alanının adını depolayan bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama, `GetName` ad için gereken arabellek boyutunu almak için yöntemi bir kez çağırır. Hata ayıklama arabelleği ayırır ve sonra arabellek doldurmak için yöntemi ikinci kez çağırır. Adın boyutunu almak için ilk arama, sorgu *modu*olarak adlandırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
