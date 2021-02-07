---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: Abort yöntemi'
title: ICorDebugEval::Abort Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: d61cb0d696a8a134d992bc8dbbfdb61103ef469f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694324"
---
# <a name="icordebugevalabort-method"></a>ICorDebugEval::Abort Yöntemi

Bu ıcorınkıımagegeval nesnesinin Şu anda gerçekleştirdiği hesaplamayı iptal eder.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Değerlendirme iç içe geçmişse ve en son bir değilse, `Abort` Yöntem başarısız olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
