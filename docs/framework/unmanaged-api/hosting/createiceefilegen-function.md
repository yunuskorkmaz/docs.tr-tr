---
title: CreateICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136831"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen İşlevi
Bir [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi oluşturur.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ceeFileGen`  
 dışı Yeni bir `ICeeFileGen` nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICeeFileGen` nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyalarını oluşturmak için kullanılır.  
  
 `ICeeFileGen` nesnesini tamamlandığında yok etmek için [Destroyııceefilegen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ICeeFileGen. h  
  
 **Kitaplık:** MSCorPE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
