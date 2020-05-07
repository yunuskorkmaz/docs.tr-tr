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
ms.openlocfilehash: 3db37576f5da7b26e7bd9d3343f8bb8b97f2ba82
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895241"
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
 'ndaki `szName` Dizinin boyutu. Bu yöntemi sorgu moduna almak için bu değeri sıfır olarak ayarlayın.  
  
 `pcchName`  
 dışı Adın boyutuna veya aslında ' de `szName`döndürülen karakter sayısına yönelik bir işaretçi. Sorgu modunda, bu değer çağıranın ad için ne kadar büyük bir arabellek ayrılacağını bilmesini sağlar.  
  
 `szName`  
 dışı Uygulama etki alanının adını depolayan bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata ayıklayıcı, `GetName` ad için gereken bir arabellek boyutunu almak üzere yöntemi bir kez çağırır. Hata ayıklayıcı arabelleği ayırır ve sonra arabelleği dolduracak ikinci kez yöntemi çağırır. Adın boyutunu almak için ilk çağrı *sorgu modu*olarak adlandırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
