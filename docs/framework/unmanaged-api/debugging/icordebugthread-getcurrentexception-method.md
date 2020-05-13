---
title: ICorDebugThread::GetCurrentException Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: 3a4da6f958407c0b704ffb7372a77b7f022fc824
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379764"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException Metodu
Yönetilen kod tarafından şu anda oluşturulmakta olan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppExceptionObject`  
 dışı `ICorDebugValue`Yönetilen kod tarafından şu anda oluşturulan özel durumu temsil eden nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel durum nesnesi, bloğun sonuna kadar özel durumun oluşturulduğu zamandan itibaren mevcut olacaktır `catch` . Icoralgıladığında Geval yöntemleri tarafından gerçekleştirilen bir işlev değerlendirmesi, kurulum 'daki özel durum nesnesini temizler ve tamamlanarak geri yükler.  
  
 Özel durumlar iç içe olabilir (örneğin, bir filtrede veya bir işlev değerlendirmesinde bir özel durum oluşturulursa), tek bir iş parçacığında birden çok bekleyen özel durum olabilir. `GetCurrentException`en güncel özel durumu döndürür.  
  
 Özel durum nesnesi ve türü özel durumun ömrü boyunca değişebilir. Örneğin, x türü bir özel durum oluşturulduktan sonra ortak dil çalışma zamanı (CLR) belleği tükendiğinden bellek dışı bir özel duruma yükseltebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
