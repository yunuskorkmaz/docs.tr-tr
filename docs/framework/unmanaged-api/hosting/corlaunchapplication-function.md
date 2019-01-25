---
title: CorLaunchApplication İşlevi
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f2a05009caed7bef6da9edee57a4a54b876b18f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580999"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication İşlevi
Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolunda uygulamayı başlatır.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwClickOnceHost`  
 [in] Değerini [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) uygulamayı başlatmadan konak türünü belirten sabit listesi.  
  
 `pwzAppFullName`  
 [in] Başlatılan uygulamanın tam adı.  
  
 `dwManifestPaths`  
 [in] Uygulama için bildirim yolları sayısı.  
  
 `ppwzManifestPaths`  
 [in] Her biri bildirim başlatılmayı uygulama için bir yol belirtir bir dizi dizeleri.  
  
 `dwActivationData`  
 [in] Başlatılan uygulama için etkinleştirme veri öğesi sayısı.  
  
 `ppwzActivationData`  
 [in] Her biri bir etkinleştirme veri öğesi başlatılmayı uygulama için olan bir dizi dizeleri.  
  
 `lpProcessInformation`  
 [out] Uygulama yüklendi işlemi hakkında bilgi için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
