---
title: IMetaDataTables Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 17305f2c088dd6f479da4c823d3db0fd50c0b3d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443226"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables Arabirimi
Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBlob Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Belirtilen sütun dizininde ikili büyük nesne (BLOB) için bir işaretçi alır.|  
|[GetBlobHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|BLOB yığınının boyutunu bayt cinsinden alır.|  
|[GetCodedTokenInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.|  
|[GetColumn Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Belirtilen tablo dizinindeki tabloda belirtilen sütun dizinindeki sütunda bulunan değerlere yönelik bir işaretçi alır.|  
|[GetColumnInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Belirtilen tabloda belirtilen sütunla ilgili verileri alır.|  
|[GetGuid Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Belirtilen dizindeki satırdan bir GUID alır.|  
|[GetGuidHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|GUID yığınının boyutunu bayt cinsinden alır.|  
|[GetNextBlob Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Tablodaki sonraki BLOBUN dizinini alır.|  
|[GetNextGuid Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Geçerli tablo sütunundaki sonraki GUID değerinin dizinini alır.|  
|[GetNextString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Geçerli tablo sütunundaki sonraki dizenin dizinini alır.|  
|[GetNextUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.|  
|[GetNumTables Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Geçerli `IMetaDataTables` örneğinin kapsamındaki tablo sayısını alır.|  
|[GetRow Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Belirtilen tablo dizinindeki tabloda belirtilen satır dizinindeki satırı alır.|  
|[GetString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.|  
|[GetStringHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Dize yığınının boyutunu bayt cinsinden alır.|  
|[GetTableIndex Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Belirtilen belirteç tarafından başvurulan tablonun dizinini alır.|  
|[GetTableInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Belirtilen tablo dizinindeki tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.|  
|[GetUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Geçerli kapsamdaki dize sütununda belirtilen dizinde sabit kodlanmış dizeyi alır.|  
|[GetUserStringHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Kullanıcı dizesi yığınının bayt cinsinden boyutunu alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
