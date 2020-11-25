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
ms.openlocfilehash: ca427439f03d92b20e7714b9724d90b240e9cecb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704077"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication İşlevi

Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  

 `dwClickOnceHost`  
 'ndaki Uygulamayı başlatan konak türünü belirten [HOST_TYPE](host-type-enumeration.md) numaralandırması değeri.  
  
 `pwzAppFullName`  
 'ndaki Başlatılmakta olan uygulamanın tam adı.  
  
 `dwManifestPaths`  
 'ndaki Uygulamanın bildirim yollarının sayısı.  
  
 `ppwzManifestPaths`  
 'ndaki Her biri, başlatılmakta olan uygulama için bir bildirimin yolunu belirten dizeler dizisi.  
  
 `dwActivationData`  
 'ndaki Başlatılmakta olan uygulama için etkinleştirme verisi öğelerinin sayısı.  
  
 `ppwzActivationData`  
 'ndaki Her biri, başlatılmakta olan uygulama için bir etkinleştirme verileri öğesi olan dizeler dizisi.  
  
 `lpProcessInformation`  
 dışı Uygulamanın yüklendiği işlem hakkındaki bilgilere yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
