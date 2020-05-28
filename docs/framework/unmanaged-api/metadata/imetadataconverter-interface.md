---
title: IMetaDataConverter Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008384"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter Arabirimi
Tür kitaplıklarını meta veri imzalarına eşlemek ve birinden diğerine dönüştürmek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo Metodu](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Belirtilen örnek tarafından başvurulan tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) örneğine yönelik bir işaretçi alır `ITypeInfo` .|  
|[GetMetaDataFromTypeLib Metodu](imetadataconverter-getmetadatafromtypelib-method.md)|`IMetaDataImport`Belirtilen örnek tarafından temsil edilen tür kitaplığı için meta veri imzasını temsil eden bir örneğe yönelik bir işaretçi alır `ITypeLib` .|  
|[GetTypeLibFromMetaData Metodu](imetadataconverter-gettypelibfrommetadata-method.md)|`ITypeLib`Belirtilen modüle ve kitaplık adlarına sahip tür kitaplığını temsil eden bir örneğe yönelik bir işaretçi alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
