---
title: "ICorDebugThread::EnumerateChains Yöntemi"
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
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e6a9637edb4a846b4d10dd6565533a9219ad558
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains Yöntemi
Arabirim işaretçisi bu Icordebugthread nesnesindeki tüm yığın zincirleri içeren bir Icordebugchainenum Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppChains`  
 [out] Adresine bir işaretçi bir `ICorDebugChainEnum` tüm yığınının numaralandırması veren nesnesi zincir etkin (diğer bir deyişle, en son) zinciri başlayarak, bu iş parçacığında.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın zinciri iş parçacığı için fiziksel çağrı yığını temsil eder. Aşağıdaki koşullarda bir yığın zinciri sınır oluşturun:  
  
-   Yönetilmeyen veya yönetilen için yönetilmeyen geçişi.  
  
-   Bir içerik anahtarı.  
  
-   Bir hata ayıklayıcı, kullanıcı iş parçacığı geçirme.  
  
 Tamamen yönetilen kod tek bir içerik içinde çalışan iş parçacığı en basit durumda, bir bire yığını zincirlerini ve iş parçacıkları arasında yer alır.  
  
 Tüm iş parçacıklarının fiziksel çağrı yığınları mantıksal çağrısı yığınlar halinde düzenlemek bir hata ayıklayıcısı isteyebilirsiniz. Bu iş parçacıkları zincirleri arayan/Aranan ilişkilerini sıralama ve bunları regrouping içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
