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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 535d94688d02a7315529d17fae555fba457bbb86
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737878"
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
 [in] Boyutu `szName` dizisi. Bu değer, bu yöntem sorgu moduna sıfıra ayarlayın.  
  
 `pcchName`  
 [out] Boyut adı ya da gerçekte döndürülen karakter sayısı için bir işaretçi `szName`. Sorgu modunda, bu değer ne büyüklükte bir arabellek bilmeniz arayan olanak tanır. adı ayrılamıyor.  
  
 `szName`  
 [out] Uygulama etki alanı adını depolar dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata ayıklayıcı çağırır `GetName` adı gerekli bir arabellek boyutunu almak için bir kez yöntemi. Hata ayıklayıcı arabelleği ayırır ve ardından arabellek doldurmak için ikinci bir kez yöntemini çağırır. Adı boyutunu almak için birinci çağrı olarak adlandırılır *sorgu modu*.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
