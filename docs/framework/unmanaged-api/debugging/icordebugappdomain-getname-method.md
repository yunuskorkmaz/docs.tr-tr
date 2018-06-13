---
title: ICorDebugAppDomain::GetName Metodu
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
ms.openlocfilehash: 84f895e749fc8f2520dbce3caf9e6c11fda78a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405775"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName Metodu
Uygulama etki alanı adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Boyutunu `szName` dizi. Bu yöntem sorgu moduna sıfıra bu değeri ayarlayın.  
  
 `pcchName`  
 [out] Boyutu adı ya da gerçekte döndürülen karakter sayısını gösteren bir işaretçi `szName`. Sorgu modunda bu değer ne kadar büyük bir arabellek bilmeniz çağıran sağlar adını ayrılamadı.  
  
 `szName`  
 [out] Uygulama etki alanı adını depolar bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata ayıklayıcısı çağırır `GetName` adı gerekli bir arabellek boyutu almak için bir kez yöntemi. Hata ayıklayıcı arabellek ayırır ve ardından arabellek doldurmak için ikinci kez yöntemini çağırır. Ad boyutunu almak için ilk çağrı olarak adlandırılır *sorgu modunu*.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
