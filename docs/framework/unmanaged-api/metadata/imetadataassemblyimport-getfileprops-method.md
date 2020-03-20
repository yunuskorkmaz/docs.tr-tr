---
title: IMetaDataAssemblyImport::GetFileProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175986"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps Metodu
Belirtilen meta veri imzasıyla dosyanın özelliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mdf`  
 [içinde] Özellikleri `mdFile` almak için dosyayı temsil eden meta veri belirteci.  
  
 `szName`  
 [çıkış] Dosyanın basit adı.  
  
 `cchName`  
 [içinde] Boyutu, geniş chars, `szName`ve .  
  
 `pchName`  
 [çıkış] Geniş karakter sayısı aslında döndü `szName`.  
  
 `ppbHashValue`  
 [çıkış] Karma değeri için bir işaretçi. Bu, SHA-1 algoritmasını kullanarak dosyanın karma.  
  
 `pcbHashValue`  
 [çıkış] Döndürülen karma değerdeki geniş karakter sayısı.  
  
 `pdwFileFlags`  
 [çıkış] Bir dosyaya uygulanan meta verileri açıklayan bayraklar için bir işaretçi. Bayrak değeri, bir veya daha fazla [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) değerinin bir leşimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
