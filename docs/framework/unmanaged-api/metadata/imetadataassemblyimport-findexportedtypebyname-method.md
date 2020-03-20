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
ms.openlocfilehash: edfe5de9c9d7ef9607a2eea5146194bbd4393a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175999"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi
Adı ve çevreleyen türü verilen dışa aktarılan bir türü işaretçialır.  
  
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
 [içinde] Dışa aktarılan türün adı.  
  
 `mdtExportedType`  
 [içinde] Dışa aktarılan türdeki enilgili sınıfın meta veri belirteci. İstenilen dışa aktarılan tür iç içe bir tür değilse, bu değerdir. `mdExportedTypeNil`  
  
 `ptkExportedType`  
 [çıkış] Dışa `mdExportedType` aktarılan türü temsil eden belirteç için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem, `FindExportedTypeByName` başvuruları çözmek için ortak dil çalışma zamanı tarafından kullanılan standart kuralları kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
