---
title: ICLRMetadataLocator::GetMetadata Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator.GetMetadata
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8758a96464d1465d92fb17314f1e36ab8d9169c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata Metodu
Görüntü meta verilerini almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `imagePath`  
 [in] Görüntü dosyasının yolunu belirten bir dize.  
  
 `imageTimestamp`  
 [in] Görüntü dosyasının zaman damgası.  
  
 `imageSize`  
 [in] Görüntü dosyasının boyutu.  
  
 `mvid`  
 [in] Görüntü genel benzersiz tanıtıcısı.  
  
 `mdRva`  
 [in] Meta veri göreli sanal adres (RAV). Görüntü taban adresi göre adresidir.  
  
 `flags`  
 [in] Gelecekte kullanılmak üzere ayrılmış.  
  
 `bufferSize`  
 [in] Meta veriler yerleştirileceği arabelleğin boyutu.  
  
 `buffer`  
 [out] Meta veriler yerleştirileceği arabelleği.  
  
 `dataSize`  
 [out] Döndürülen meta veri boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRMetadataLocator Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
