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
ms.openlocfilehash: 50ec5a23db4d2460480bcc3e463ecd88e7470bde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134529"
---
# <a name="getassemblyidentityfromfile-function"></a>GetAssemblyIdentityFromFile İşlevi
Belirtilen dosya yolundaki derlemede belirtilen `IID` sahip bir `IUnknown` nesnesine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki Döndürülecek arabirimin `IID`.  
  
 `ppIdentity`  
 dışı Döndürülen arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IUnknown](/cpp/atl/iunknown)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
