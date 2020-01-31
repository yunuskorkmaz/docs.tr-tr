---
title: ICLRMetadataLocator::GetMetadata Metodu
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: 66b3934d000b4f000c368acb1f57c8fc82a5c453
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793619"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata Metodu
Bir görüntünün meta verilerini almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `imagePath`  
 'ndaki Görüntü dosyasının yolunu belirten bir dize.  
  
 `imageTimestamp`  
 'ndaki Görüntü dosyasının zaman damgası.  
  
 `imageSize`  
 'ndaki Resim dosyasının boyutu.  
  
 `mvid`  
 'ndaki Görüntünün genel benzersiz tanımlayıcısı.  
  
 `mdRva`  
 'ndaki Meta verilerin göreli sanal adresi (RVA). Adres, görüntü temel adresiyle ilişkilidir.  
  
 `flags`  
 'ndaki Gelecekte kullanılmak üzere ayrılmıştır.  
  
 `bufferSize`  
 'ndaki Meta verilerin yerleştirileceği arabelleğin boyutu.  
  
 `buffer`  
 dışı Meta verilerin yerleştirileceği arabellek.  
  
 `dataSize`  
 dışı Döndürülen meta verilerin boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetadataLocator Arabirimi](iclrmetadatalocator-interface.md)
