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
ms.openlocfilehash: c35baaee13782566c64dd8447c6a034f699b5cd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667008"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject Yöntemi
Yeni bir parametreli tür nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
