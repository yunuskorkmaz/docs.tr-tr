---
title: "CloseCLREnumeration İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f6de2d1625b4d9f66ec27ad7ed3e6ba33cc59b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration İşlevi
İşleyici tarafından döndürülen bir dizi bulunan geçerli ortak dil çalışma zamanı (CLR) devam başlangıç olaylara kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcısı ve dize yolu diziler için bellek boşaltır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pHandleArray`  
 [in] Olay tanıtıcıları dizisi işaretçi döndürdü [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] CLR dize yolları döndürülen dizi işaretçi [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] Boyutunu (uzunluk) ya da içeren DWORD `pHandleArray` veya `pStringArray` (bunlar aynıdır).  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Tanıtıcıları açan [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) kapalı olduğundan ve işleyici ve dize diziler için ayrılan belleği serbest.  
  
 E_INVALIDARG  
 Uzunluğu `pHandleArray` geçirilen uzunluğu eşleşmiyor `dwArrayLength`.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 İşlev için belleği serbest alamıyor `pHandleArray` ve `pStringArray`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
