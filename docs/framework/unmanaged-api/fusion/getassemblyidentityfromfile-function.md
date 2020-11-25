---
title: GetAssemblyIdentityFromFile İşlevi
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 9580dd3bc5a7279549e8deadac95d35a33da74f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724487"
---
# <a name="getassemblyidentityfromfile-function"></a>GetAssemblyIdentityFromFile İşlevi

`IUnknown`Belirtilen dosya yolundaki derlemede belirtilen bir nesneye yönelik bir işaretçi alır `IID` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a>Parametreler  

 `pwzFilePath`  
 'ndaki İstenen derleme için geçerli bir yol.  
  
 `riid`  
 'ndaki `IID` Döndürülecek arabirim.  
  
 `ppIdentity`  
 dışı Döndürülen arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IUnknown](/cpp/atl/iunknown)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
