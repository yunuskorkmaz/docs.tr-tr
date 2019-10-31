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
ms.openlocfilehash: 38fe50f5a6608bb27d7a7818dee4784a7f8113ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133601"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains Yöntemi
Bu ICorDebugThread nesnesindeki tüm yığın zincirlerini içeren bir ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppChains`  
 dışı Bu iş parçacığında, etkin (yani en son) zincirden başlayarak tüm yığın zincirlerinin numaralandırılmasına izin veren bir `ICorDebugChainEnum` nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın zinciri, iş parçacığının fiziksel çağrı yığınını temsil eder. Aşağıdaki koşullar bir yığın zinciri sınırı oluşturur:  
  
- Yönetilmeyenden yönetilene veya yönetilmeyen bir geçişe.  
  
- Bir bağlam anahtarı.  
  
- Bir kullanıcı iş parçacığını bir hata ayıklayıcı ele geçirme.  
  
 Tek bir bağlamda tamamen yönetilen kod çalıştıran bir iş parçacığı için basit durumda, iş parçacıkları ve yığın zincirleri arasında bire bir yazışmaya sahip olur.  
  
 Bir hata ayıklayıcı, tüm iş parçacıklarının fiziksel çağrı yığınlarını mantıksal çağrı yığınlarına yeniden düzenlemek isteyebilir. Bu, tüm iş parçacıklarının zincirlerini arayan/çağrılan ilişkilerine göre sıralamayı ve yeniden gruplandırmayı kapsar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
