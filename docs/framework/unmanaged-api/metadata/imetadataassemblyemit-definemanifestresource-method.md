---
title: IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177866"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
Belirtilen bildirim `ManifestResource` kaynağı için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirteci döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szName`  
 [içinde] Kaynağın adı.  
  
 `tkImplementation`  
 [içinde] Bir meta veri türü `mdtFile` `mdtAssemblyRef` belirteci veya kaynak sağlayıcısı yla eşler. NULL değeri, meta verilerin katıştırıldığı dosyanın kaynak sağlayıcısı olduğunu gösterir.  
  
 `dwOffset`  
 [içinde] Dosya içindeki kaynağın başına mahsup. Bağımsız dosyalardaki kaynaklar için bu her zaman sıfır olacaktır. Kaynak bir PE (taşınabilir çalıştırılabilir) dosyaya katıştırılmışsa, bu, cor.h üstbilgi dosyasında belirtilen konumda başlayan kaynak BLOB'nin bir mahsup noktasıdır.  
  
 `dwResourceFlags`  
 [içinde] Kaynak tanımı için özellik ayarlarını belirten bayrak değerlerinin bityişli bir leşimi.  
  
 `pmdmr`  
 [çıkış] Döndürülen meta veri belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Derlemenin her dosyasında uygulanan her kaynak için bir `ManifestResource` meta veri yapısı tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
