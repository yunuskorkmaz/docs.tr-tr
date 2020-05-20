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
ms.openlocfilehash: 57508a2df3a49c39d25347f2a3038442c37278da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616768"
---
# <a name="coinitializeee-function"></a>CoInitializeEE İşlevi
Ortak dil çalışma zamanı yürütme altyapısının bir işleme yüklenmesini sağlar. Bu işlev .NET Framework 4 ' te kullanım dışıdır. Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fFlags`  
 'ndaki [Coinitiee](../metadata/coinitiee-enumeration.md) sabit listesi sabitlerinden biri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, Winerror. h içinde tanımlanan standart COM hata kodlarını ve aşağıdaki tabloda bulunan değerleri döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yürütme altyapısı başarıyla yüklendi.|  
|S_FALSE|Yürütme altyapısı zaten yüklü.|  
|E_FAIL|Yürütme altyapısı yüklenemedi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, daha önce yüklenmediyse yürütme altyapısını yükler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../metadata/metadata-global-static-functions.md)
