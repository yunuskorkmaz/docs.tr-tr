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
ms.openlocfilehash: 4eb878b61b72378bc6870af7f2cd09f0b6943b13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136497"
---
# <a name="destroyiceefilegen-function"></a>DestroyICeeFileGen İşlevi
Bir [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesini yok eder.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ceeFileGen`  
 'ndaki Yok edilecek `ICeeFileGen` nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `DestroyICeeFileGen` [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) işlevi tarafından oluşturulan `ICeeFileGen` nesnesini yok eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ICeeFileGen. h  
  
 **Kitaplık:** MSCorPE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
