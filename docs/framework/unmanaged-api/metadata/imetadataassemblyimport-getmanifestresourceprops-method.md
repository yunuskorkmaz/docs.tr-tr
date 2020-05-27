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
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009034"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi
Belirtilen meta veri imzasıyla bildirim kaynağının özellik kümesini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `mdManifestResource`Özelliklerinin alınacağı kaynağı temsil eden bir belirteç.  
  
 `szName`  
 dışı Kaynağın adı.  
  
 `cchName`  
 'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .  
  
 `pchName`  
 dışı Aslında ' de döndürülen geniş karakter sayısının bir işaretçisi `szName` .  
  
 `ptkImplementation`  
 dışı `mdFile` `mdAssemblyRef` Kaynağı içeren, sırasıyla, dosya veya derlemeyi temsil eden belirtece veya belirtece yönelik bir işaretçi.  
  
 `pdwOffset`  
 dışı Dosyanın içindeki kaynağın başlangıcına olan sapmayı belirten bir değer işaretçisi.  
  
 `pdwResourceFlags`  
 dışı Bir kaynağa uygulanan meta verileri tanımlayan bayrakların işaretçisi. Flags değeri bir veya daha fazla [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) değeri birleşimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
