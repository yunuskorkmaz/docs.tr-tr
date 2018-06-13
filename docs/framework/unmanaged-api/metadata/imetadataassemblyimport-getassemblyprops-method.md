---
title: IMetaDataAssemblyImport::GetAssemblyProps Metodu
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
ms.openlocfilehash: 911d0d1444e2cf3cb8241eeeff63a5a86b4ab806
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446280"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps Metodu
Belirtilen meta veri imzayla derleme için özellikler kümesini alır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `mda`  
 [in]. `mdAssembly` Özellikleri almak istediğiniz bütünleştirilmiş kod gösteren meta veri simgesi.  
  
 `ppbPublicKey`  
 [out] Ortak anahtar veya meta veri simgesi için bir işaretçi.  
  
 `pcbPublicKey`  
 [out] Döndürülen ortak anahtar bayt sayısı.  
  
 `pulHashAlgId`  
 [out] Derleme dosyalarında karması için kullanılan algoritma için bir işaretçi.  
  
 `szName`  
 [out] Derleme basit adı.  
  
 `cchName`  
 [in] Geniş karakter boyutu, `szName`.  
  
 `pchName`  
 [out] Gerçekte döndürülen geniş karakter sayısı `szName`.  
  
 `pMetaData`  
 [out] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısı için bir işaretçi.  
  
 `pdwAssemblyFlags`  
 [out] Bir derlemeye uygulanan meta verileri açıklayan bayrakları. Bu değer bir veya daha fazla birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
