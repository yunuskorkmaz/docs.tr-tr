---
description: 'Daha fazla bilgi edinin: ICorDebugThread4:: HadUnhandledException yöntemi'
title: ICorDebugThread4::HadUnhandledException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: cd0ccdbdd68c37b5fbdbd705da7136e5d36baa60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800935"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException Yöntemi

İş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppBlockingObjectEnum`  
 dışı [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı numaralandırmanın adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|İş parçacığında oluşturulduktan sonra işlenmeyen bir özel durum oluştu.|  
|S_FALSE|İş parçacığında işlenmeyen bir özel durum yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, iş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir. İşlenmeyen özel durum geri çağrısının tetiklendiği veya yerel JıT-Attach başlatıldığı zaman, bu yöntemin S_OK döndürmesi garanti edilir. [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) yönteminin işlenmemiş özel durumu döndürmeyeceği garantisi yoktur; Ancak, işlenmeyen özel durum geri çağırması alındıktan sonra veya yerel JıT-Attach sonrasında işlem henüz devam ettirilmemişse olur. Ayrıca, yerel JıT-iliştirme tetiklendiğinde işlenmemiş bir özel durumla birden fazla iş parçacığına sahip olması mümkündür. Böyle bir durumda, JıT-Attach ' i tetikleyen özel durumu belirlemenin bir yolu yoktur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugThread4 Arabirimi](icordebugthread4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
