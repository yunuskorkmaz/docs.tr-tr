---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08bf4022f7cd7f85ffe7939c16fd47950e131a77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948908"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu
Bir başvuru işaretçi, tanıtıcı bir çöp toplama olan belirtilen yönetilen nesneyi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `handle`  
 [in] Bir çöp toplama tanıtıcı olan yönetilen bir nesneye bir işaretçi. Bu değer bir <xref:System.IntPtr> nesne ve alınabilir <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne.  
  
 `pOutValue`  
 [out] Bir işaretçi adresine Icordebugreferencevalue nesnenin belirtilen yönetilen nesneye bir başvuruyu temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen başvuru değeri bir çöp toplama başvuru değeri ile karıştırmayın.  
  
 Döndürülen başvuru, normal bir başvurusu gibi davranır. Kod yürütmeyi bir kesme noktası sonra devam ettiğinde devre dışı bırakıldı. Hedef nesnenin ömrünü başvuru değeri ömrünü tarafından etkilenmez.  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle` Yöntemi tanıtıcı doğrulamaz. Bu nedenle, `GetReferenceValueFromGCHandle` yöntemi büyük olasılıkla bozulmasına neden olabilir hem hata ayıklayıcı hem de Geçersiz tanıtıcı iletilmezse ayıklanan kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
