---
description: ': ICorDebugThread:: Enumeratezincirleri yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b9184a1b298e1d29970c5e56ceca76715b0ed096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659302"
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
 dışı `ICorDebugChainEnum` Bu iş parçacığında, etkin (yani en son) zincirden başlayarak tüm yığın zincirlerinin numaralandırılmasına izin veren nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Yığın zinciri, iş parçacığının fiziksel çağrı yığınını temsil eder. Aşağıdaki koşullar bir yığın zinciri sınırı oluşturur:  
  
- Yönetilmeyenden yönetilene veya yönetilmeyen bir geçişe.  
  
- Bir bağlam anahtarı.  
  
- Bir kullanıcı iş parçacığını bir hata ayıklayıcı ele geçirme.  
  
 Tek bir bağlamda tamamen yönetilen kod çalıştıran bir iş parçacığı için basit durumda, iş parçacıkları ve yığın zincirleri arasında bire bir yazışmaya sahip olur.  
  
 Bir hata ayıklayıcı, tüm iş parçacıklarının fiziksel çağrı yığınlarını mantıksal çağrı yığınlarına yeniden düzenlemek isteyebilir. Bu, tüm iş parçacıklarının zincirlerini arayan/çağrılan ilişkilerine göre sıralamayı ve yeniden gruplandırmayı kapsar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
