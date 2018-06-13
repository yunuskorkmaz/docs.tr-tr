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
ms.openlocfilehash: 7a53b0a9cdcec33846f9d491e7d6567bcf9235b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428768"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication İşlevi
Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
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
 [in] Değerini [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) numaralandırma Uygulama başlatılmadan ana bilgisayar türünü belirtir.  
  
 `pwzAppFullName`  
 [in] Başlatılır uygulamanın tam adı.  
  
 `dwManifestPaths`  
 [in] Uygulama için bildirim yolları sayısı.  
  
 `ppwzManifestPaths`  
 [in] Her biri başlatılır uygulama için bir bildirim yolunu belirtir, bir dizi dizeleri.  
  
 `dwActivationData`  
 [in] Başlatılır uygulama için etkinleştirme veri öğesi sayısı.  
  
 `ppwzActivationData`  
 [in] Her biri başlatılır uygulama için bir etkinleştirme veri öğesi olan bir dize dizisi.  
  
 `lpProcessInformation`  
 [out] Uygulama yüklendi işlemi hakkında bilgi için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
