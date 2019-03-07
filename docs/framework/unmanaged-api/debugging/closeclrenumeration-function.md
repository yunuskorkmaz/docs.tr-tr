---
title: CloseCLREnumeration İşlevi
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60b6d9c302cd3af9f41e5a8dce62d7eb268c4198
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491883"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration İşlevi
Bir dizi tarafından döndürülen tanıtıcı bulunan geçerli ortak dil çalışma zamanı (CLR) devam başlangıç olaylara kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcı ve dize yolu diziler için belleği serbest bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pHandleArray`  
 [in] Sağlayıcıdan döndürülen olay tanıtıcı dizisine işaretçisine [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] CLR dize yolları öğesinden döndürülen bir dizi işaretçi [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] Boyutu (uzunluk) ya da içeren DWORD `pHandleArray` veya `pStringArray` (bunlar aynıdır).  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Tanıtıcıları açan [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) kapalı olduğundan ve tanıtıcı ve dize diziler için ayrılan belleği serbest.  
  
 E_INVALIDARG  
 Uzunluğunu `pHandleArray` geçirilen uzunluğu eşleşmiyor `dwArrayLength`.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 İşlev için belleği serbest silemiyor `pHandleArray` ve `pStringArray`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
