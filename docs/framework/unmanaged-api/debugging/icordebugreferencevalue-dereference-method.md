---
description: ': ICorDebugReferenceValue::D ereference yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugReferenceValue::Dereference Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: af225f746a9c67a90a7ad73046cd03401e4ba735
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691113"
---
# <a name="icordebugreferencevaluedereference-method"></a>ICorDebugReferenceValue::Dereference Yöntemi

Başvurulan nesneyi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppValue`  
 dışı Bu ICorDebugReferenceValue nesnesinin işaret ettiği nesneyi temsil eden ICorDebugValue 'ın adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugValue`Nesne yalnızca başvurusu henüz devre dışı bırakılmadıysa geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
