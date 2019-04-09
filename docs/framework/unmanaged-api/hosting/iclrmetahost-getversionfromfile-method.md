---
title: ICLRMetaHost::GetVersionFromFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6c7fd48269a3e8291a548b3e13efe5c8e70652
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150819"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile Metodu
Verilen dosya yoluna (meta verilerinde depolanır), bir derlemenin özgün .NET Framework derleme sürümü alır. Bu yöntem yerine geçer [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzFilePath`  
 [in] Tam derleme dosya yolu.  
  
 `pwzbuffer`  
 [out] .NET Framework derleme sürümü biçiminde meta verilerde depolanan "v*A*. *B*[. *X*] ". *A*, *B*, ve *X* ana sürüm, ikincil sürüm ve derleme numarasını karşılık gelen ondalık sayılardır. Bu dizenin uzunluğu için MAX_PATH sınırlıdır.  
  
> [!NOTE]
>  Bu çıkış C:\Windows\Microsoft.NET\Framework altında göründüğü gibi .NET Framework sürümü için dizin adı ile eşleşir.  
  
 Örnek değerler şunlardır: "v1.0.3705", "v1.1.4322", "v2.0.50727" ve "v4.0. *X*"burada *X* yüklü derleme sayısına bağlıdır. "V" ön eki gerekli olduğunu unutmayın.  
  
 `pcchBuffer`  
 [out içinde] Boyutu `pwzbuffer` arabellek taşması önlemek için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzbuffer` veya `pcchBuffer` null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Arabellek çok küçük.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
