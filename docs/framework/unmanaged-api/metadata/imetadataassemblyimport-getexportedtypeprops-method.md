---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: GetExportedTypeProps yöntemi'
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
ms.openlocfilehash: 894fb65fb6de76a218489b2a85a2d3c20c572789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784125"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps Metodu

Belirtilen meta veri imzasıyla, dışarıya aktarılmış türün özelliklerinin kümesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  

 `mdct`  
 'ndaki `mdExportedType` İçe aktarılmış türü temsil eden bir meta veri belirteci.  
  
 `szName`  
 dışı İçe aktarılmış türün adı.  
  
 `cchName`  
 'ndaki Öğesinin geniş karakterdeki boyutu `szName` .  
  
 `pchName`  
 dışı Aslında içinde döndürülen geniş karakter sayısı `szName`  
  
 `ptkImplementation`  
 dışı Bir `mdFile` , `mdAssemblyRef` veya, bir veya daha fazla `mdExportedType` içe aktarılmış türün özelliklerine erişim izni veren bir meta veri belirteci.  
  
 `ptkTypeDef`  
 dışı `mdTypeDef` Dosyadaki bir türü temsil eden belirtece yönelik bir işaretçi.  
  
 `pdwExportedTypeFlags`  
 dışı İçe aktarılmış türe uygulanan meta verileri tanımlayan bayrakların işaretçisi. Bayrak değeri bir veya daha fazla [CorTypeAttr](cortypeattr-enumeration.md) değeri olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
