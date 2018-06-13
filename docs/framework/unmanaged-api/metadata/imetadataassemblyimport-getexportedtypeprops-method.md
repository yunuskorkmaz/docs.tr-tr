---
title: IMetaDataAssemblyImport::GetExportedTypeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c76e46c75680d9fc0ad70e94da288f0c6b5e5ee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446326"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps Metodu
Belirtilen meta veri imzayla verilen türünün özelliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mdct`  
 [in] Bir `mdExportedType` dışarı aktarılan türünü temsil eden meta veri simgesi.  
  
 `szName`  
 [out] Dışarı aktarılan türünün adı.  
  
 `cchName`  
 [in] Geniş karakterler boyutu, `szName`.  
  
 `pchName`  
 [out] Gerçekte döndürülen geniş karakter sayısı `szName`  
  
 `ptkImplementation`  
 [out] Bir `mdFile`, `mdAssemblyRef`, veya `mdExportedType` içeren veya erişime izin verilen türünün özelliklerini meta veri simgesi.  
  
 `ptkTypeDef`  
 [out] Bir işaretçi bir `mdTypeDef` dosyasındaki bir türü temsil eden belirteci.  
  
 `pdwExportedTypeFlags`  
 [out] Dışarı aktarılan türüne uygulanacağını meta verileri açıklayan bayrakları gösteren bir işaretçi. Bayrak değeri bir veya daha fazla olabilir [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) değerleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
