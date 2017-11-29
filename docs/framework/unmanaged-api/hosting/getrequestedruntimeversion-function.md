---
title: "GetRequestedRuntimeVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersion
helpviewer_keywords: GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bfac4e32841b8a8332a1f4124c1326f1ef7da1f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion İşlevi
Belirtilen uygulama tarafından istenen ortak dil çalışma zamanı (CLR) sürüm numarasını alır. Bu sürümü yüklü değilse, önce istenen sürümü yüklü en son sürümünü alır.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pExe`  
 [in] Uygulamanın adı.  
  
 `pVersion`  
 [out] Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabellek.  
  
 `cchBuffer`  
 [in] Sürüm arabellek uzunluğu.  
  
 `pdwLength`  
 [out] Sürüm numarası dize uzunluğu için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|ERROR_INSUFFICIENT_BUFFER|Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.|  
|E_POINTER|`pdwLength`null şeklindedir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Getrequestedruntimeınfo işlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [GetVersionFromProcess işlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
