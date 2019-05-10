---
title: ICorDebugThread::EnumerateChains Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f131f7566376d6474f3189d5eb612b30bec2e2b7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648432"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains Yöntemi
Bu Icordebugthread nesnesindeki tüm yığın zincirlerini içeren bir Icordebugchainenum Numaralandırıcı için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppChains`  
 [out] Adresine bir işaretçi bir `ICorDebugChainEnum` etkin (diğer bir deyişle, en son) halkasını başlayarak, bu iş parçacığındaki tüm yığın numaralandırma veren nesnesi zincir.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın zincirinin iş parçacığı için fiziksel çağrı yığınını temsil eder. Aşağıdaki durumlarda bir yığın zincirinin sınırı oluşturun:  
  
- Yönetilmeyen veya yönetilene geçiş.  
  
- Bir içerik anahtarı.  
  
- Bir hata ayıklayıcı, bir kullanıcı iş parçacığının geçirme.  
  
 En basit durumda tek bir bağlamda yalnızca yönetilen kod çalıştıran iş parçacığı yığın zincirlerini ve iş parçacıkları arasında bire bir iletişimin sunulacaktır.  
  
 Bir hata ayıklayıcı, tüm iş parçacıklarının fiziksel çağrı yığınlarını mantıksal çağrı yığınlarını yeniden isteyebilirsiniz. Bu, tüm iş parçacıkları zincirleri çağıran/çağrılan ilişkilerine göre sıralama ve bunları regrouping içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
