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
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771105"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains Yöntemi
Bu Icordebugthread nesnesindeki tüm yığın zincirlerini içeren bir Icordebugchainenum Numaralandırıcı için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
