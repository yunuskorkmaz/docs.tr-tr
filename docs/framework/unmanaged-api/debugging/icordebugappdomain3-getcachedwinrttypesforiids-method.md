---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 8b259636a8bd28abd3bba12c4a05dda3c13557e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784899"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi
Bir uygulama etki alanındaki önbelleğe alınmış Windows Çalışma Zamanı türleri için kendi arabirim tanımlayıcılarına göre bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cReqTypes`  
 'ndaki Gerekli türlerin sayısı.  
  
 `iidsToResolve`  
 'ndaki Alınacak Windows Çalışma Zamanı türlerinin yönetilen temsillerine karşılık gelen arabirim tanımlayıcılarını içeren bir dizi işaretçisi.  
  
 `ppTypesEnum`  
 dışı Bir "ICorDebugTypeEnum" arabirim nesnesinin, `iidsToResolve`içindeki arabirim tanımlayıcılarına göre alınan Windows Çalışma Zamanı türlerinin önbelleğe alınmış yönetilen temsillerine yönelik numaralandırılmasına izin veren bir.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem belirli bir arabirim tanımlayıcısı için bilgileri alamadığında, "ICorDebugTypeEnum" koleksiyonundaki karşılık gelen giriş, veri alımı sorunları veya bilinmeyen arabirim tanımlayıcıları için `ELEMENT_TYPE_VOID` bir tür `ELEMENT_TYPE_END` olacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Windows Çalışma Zamanı  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugAppDomain3 Arabirimi](icordebugappdomain3-interface.md)
