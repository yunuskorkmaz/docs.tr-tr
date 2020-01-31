---
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
ms.openlocfilehash: f558a4c94afeb69f58605958ddcb91e4be772c39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791348"
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
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İş parçacığında oluşturulduktan sonra işlenmeyen bir özel durum oluştu.|  
|S_FALSE|İş parçacığında işlenmeyen bir özel durum yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, iş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir. İşlenmeyen özel durum geri çağrısının tetiklendiği veya yerel JıT-Attach başlatıldığı zaman, bu yöntemin S_OK döndürmesi garanti edilir. [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) yönteminin işlenmemiş özel durumu döndürmeyeceği garantisi yoktur; Ancak, işlenmeyen özel durum geri çağırması alındıktan sonra veya yerel JıT-Attach sonrasında işlem henüz devam ettirilmemişse olur. Ayrıca, yerel JıT-iliştirme tetiklendiğinde işlenmemiş bir özel durumla birden fazla iş parçacığına sahip olması mümkündür. Böyle bir durumda, JıT-Attach ' i tetikleyen özel durumu belirlemenin bir yolu yoktur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugThread4 Arabirimi](icordebugthread4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
