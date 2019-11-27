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
ms.openlocfilehash: c1792ed0f15f8cfb62567593c9694453650f0bb9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436322"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi
Belirtilen meta veri imzasıyla bildirim kaynağının özellik kümesini alır.  
  
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
 'ndaki Özelliklerinin alınacağı kaynağı temsil eden `mdManifestResource` belirteç.  
  
 `szName`  
 dışı Kaynağın adı.  
  
 `cchName`  
 'ndaki `szName`geniş karakter cinsinden boyutu.  
  
 `pchName`  
 dışı `szName`' de döndürülen geniş karakter sayısının bir işaretçisi.  
  
 `ptkImplementation`  
 dışı Kaynağı içeren, sırasıyla dosyayı veya derlemeyi temsil eden bir `mdFile` belirtecinin veya `mdAssemblyRef` belirtecinin işaretçisi.  
  
 `pdwOffset`  
 dışı Dosyanın içindeki kaynağın başlangıcına olan sapmayı belirten bir değer işaretçisi.  
  
 `pdwResourceFlags`  
 dışı Bir kaynağa uygulanan meta verileri tanımlayan bayrakların işaretçisi. Flags değeri bir veya daha fazla [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değeri birleşimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
