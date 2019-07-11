---
title: ICorDebugEval2::NewParameterizedObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae5f4c79acd6f92d42c2890ba64fa66e1b4bfbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753593"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject Yöntemi
Yeni bir parametreli tür nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pConstructor`  
 [in] Oluşturulacak nesnenin oluşturucusunun temsil eden bir ICorDebugFunction nesne işaretçisi.  
  
 `nTypeArgs`  
 [in] Tür bağımsız değişkenleri geçirildi.  
  
 `ppTypeArgs`  
 [in] Her biri örneği oluşturulan nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesneye işaret eden bir işaretçiler dizisi.  
  
 `nArgs`  
 [in] Bağımsız değişkenlerin sayısı, oluşturucuya geçirilen.  
  
 `ppArgs`  
 [in] Oluşturucuya geçirilen bir bağımsız değişken değeri temsil eden bir Icordebugvalue nesne işaret her biri bir işaretçiler dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Nesnenin oluşturucusunun sürebilir <xref:System.Type> parametreleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
