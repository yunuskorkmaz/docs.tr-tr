---
title: IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177656"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi
Belirtilen meta veri imzasıyla bildirim kaynağının özellikleri kümesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mdmr`  
 [içinde] Özellikleri `mdManifestResource` almak için kaynağı temsil eden bir belirteç.  
  
 `szName`  
 [çıkış] Kaynağın adı.  
  
 `cchName`  
 [içinde] Boyutu, geniş chars, `szName`ve .  
  
 `pchName`  
 [çıkış] Geniş karakter sayısına işaretçi aslında `szName`döndürülür.  
  
 `ptkImplementation`  
 [çıkış] Kaynağı içeren `mdFile` dosya yı `mdAssemblyRef` veya derlemeyi temsil eden bir belirteç veya belirteç için işaretçi.  
  
 `pdwOffset`  
 [çıkış] Dosya içindeki kaynağın başına mahsup belirten bir değer için işaretçi.  
  
 `pdwResourceFlags`  
 [çıkış] Kaynağa uygulanan meta verileri açıklayan bayraklar için bir işaretçi. Bayrak değeri, bir veya daha fazla [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değerinin bir leşimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
