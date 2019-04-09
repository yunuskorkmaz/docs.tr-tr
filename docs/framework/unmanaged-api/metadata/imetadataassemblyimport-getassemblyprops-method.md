---
title: IMetaDataAssemblyImport::GetAssemblyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4817a62d276bfdb50bfcbf658f40f5568673bea0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163221"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps Yöntemi
Belirtilen meta veri imzası ile derleme için özellikler kümesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mda`  
 [in]. `mdAssembly` Özelliklerini alınacağı derlemeyi temsil eden bir meta veri belirteci.  
  
 `ppbPublicKey`  
 [out] Ortak anahtarı veya meta veri belirteci için bir işaretçi.  
  
 `pcbPublicKey`  
 [out] Döndürülen ortak anahtarı bayt sayısı.  
  
 `pulHashAlgId`  
 [out] Derleme dosyaları karma yapmak için kullanılan algoritma için bir işaretçi.  
  
 `szName`  
 [out] Derlemenin basit adını.  
  
 `cchName`  
 [in] Geniş karakter, boyutunu, `szName`.  
  
 `pchName`  
 [out] Gerçekte döndürülen geniş karakter sayısını `szName`.  
  
 `pMetaData`  
 [out] Derleme meta verileri içeren bir ASSEMBLYMETADATA yapısı işaretçisi.  
  
 `pdwAssemblyFlags`  
 [out] Bir derlemeye uygulanan meta verileri tanımlayan bayraklar. Bu değer bir veya daha fazla birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
