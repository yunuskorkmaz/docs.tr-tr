---
title: DestroyICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 495d84470c559df13ea64b63dd00582f4335d4e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673202"
---
# <a name="destroyiceefilegen-function"></a>DestroyICeeFileGen İşlevi

Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ceeFileGen`  
 'ndaki `ICeeFileGen` Yok edilecek nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  

 `DestroyICeeFileGen``ICeeFileGen` [CreateICeeFileGen](createiceefilegen-function.md) işlevi tarafından oluşturulan nesneyi yok eder.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ICeeFileGen. h  
  
 **Kitaplık:** MSCorPE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
