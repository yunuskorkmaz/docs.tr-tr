---
title: CoInitializeEE İşlevi
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131937"
---
# <a name="coinitializeee-function"></a>CoInitializeEE İşlevi
Ortak dil çalışma zamanı yürütme altyapısının bir işleme yüklenmesini sağlar. Bu işlev .NET Framework 4 ' te kullanım dışıdır. Bunun yerine [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fFlags`  
 'ndaki [Coinitiee](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) sabit listesi sabitlerinden biri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, Winerror. h içinde tanımlanan standart COM hata kodlarını ve aşağıdaki tabloda bulunan değerleri döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yürütme altyapısı başarıyla yüklendi.|  
|S_FALSE|Yürütme altyapısı zaten yüklü.|  
|E_FAıL|Yürütme altyapısı yüklenemedi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, daha önce yüklenmediyse yürütme altyapısını yükler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
