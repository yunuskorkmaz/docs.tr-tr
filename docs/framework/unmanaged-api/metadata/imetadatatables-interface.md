---
title: IMetaDataTables Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff70e99a963c929792a73cefd6e8feaefa8b252e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables-interface"></a>IMetaDataTables Arabirimi
Depolama ve meta veri bilgileri tablolardaki alınması için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBlob Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Bir işaretçi ikili büyük nesne (BLOB) için belirtilen sütun dizininde alır.|  
|[GetBlobHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|BLOB yığın bayt cinsinden boyutu alır.|  
|[GetCodedTokenInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Belirtilen satır dizini ile ilişkili belirteçleri dizisi için bir işaretçi alır.|  
|[GetColumn Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Belirtilen sütun dizininde tablonun belirtilen tablo dizinindeki sütunda bulunan değerlerin için bir işaretçi alır.|  
|[GetColumnInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Belirtilen tabloda belirtilen sütun hakkındaki verileri alır.|  
|[GetGuid Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Belirtilen dizindeki satırdan bir GUID alır.|  
|[GetGuidHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|GUID yığın bayt cinsinden boyutu alır.|  
|[GetNextBlob Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Tabloda sonraki BLOB dizinini alır.|  
|[GetNextGuid Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.|  
|[GetNextString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Sonraki dizenin dizini geçerli bir tablo sütununda alır.|  
|[GetNextUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Sonraki sabit kodlanmış dize geçerli tablo sütununda içeren satırın dizinini alır.|  
|[GetNumTables Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Geçerli kapsamda tablo sayısını alır `IMetaDataTables` örneği.|  
|[GetRow Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Belirtilen satır dizininde belirtilen tablo dizinindeki tablosundaki satır alır.|  
|[GetString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Dize belirtilen dizindeki geçerli başvuru kapsamda tablo sütunuyla bağlantısı alır.|  
|[GetStringHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Dize yığın bayt cinsinden boyutu alır.|  
|[GetTableIndex Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Belirtilen belirteç tarafından başvurulan tablo için dizinini alır.|  
|[GetTableInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Ad, satır boyutu, satır sayısı, sütun sayısı ve tablo anahtar sütun dizini belirtilen tablo dizininde alır.|  
|[GetUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Geçerli kapsamdaki dize sütununda belirtilen dizindeki sabit kodlanmış dize alır.|  
|[GetUserStringHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Kullanıcı dize yığın bayt cinsinden boyutu alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
