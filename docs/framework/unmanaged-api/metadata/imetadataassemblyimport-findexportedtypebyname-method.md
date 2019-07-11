---
title: IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a70c041bc17f58a5e17877dd2e1f2aa2944e689
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777925"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi
Bir işaretçi verilen bir tür için adı ve türü kapsayan verilen alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szName`  
 [in] Dışarı aktarılan tür adı.  
  
 `mdtExportedType`  
 [in] Dışarı aktarılan tür kapsayan sınıfı için meta veri belirteci. Bu değer `mdExportedTypeNil` istenen dışarı aktardıysanız türü iç içe geçmiş bir tür değil.  
  
 `ptkExportedType`  
 [out] Bir işaretçi `mdExportedType` dışarı aktarılan türünü temsil eden belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 `FindExportedTypeByName` Yöntemi başvurularını çözümlemek için ortak dil çalışma zamanı tarafından kullanılan standart kurallar kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
