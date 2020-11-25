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
ms.openlocfilehash: b1672d98d76241e5af4b6b60a38785f1278e15a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731598"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName Yöntemi

Adı ve kapsayan türü verilen, verilen bir türe yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szName`  
 'ndaki İçe aktarılmış türün adı.  
  
 `mdtExportedType`  
 'ndaki İçe aktarılmış türün kapsayan sınıfına ait meta veri belirteci. Bu değer, `mdExportedTypeNil` istenen dışarıya alınan türün iç içe bir tür olmaması durumunda olur.  
  
 `ptkExportedType`  
 dışı Bir belirteç için, `mdExportedType` dışarıya eklenen türü temsil eden bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `FindExportedTypeByName`Yöntemi, başvuruları çözümlemek için ortak dil çalışma zamanı tarafından çalıştırılan standart kuralları kullanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../deployment/how-the-runtime-locates-assemblies.md)
