---
title: IMetaDataTables Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables
helpviewer_keywords: IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c89d615fbeeff4a60eb386d58c573ee7905f538d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables-interface"></a>IMetaDataTables Arabirimi
Depolama ve meta veri bilgileri tablolardaki alınması için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBlob yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Bir işaretçi ikili büyük nesne (BLOB) için belirtilen sütun dizininde alır.|  
|[GetBlobHeapSize yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|BLOB yığın bayt cinsinden boyutu alır.|  
|[Getcodedtokenınfo yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Belirtilen satır dizini ile ilişkili belirteçleri dizisi için bir işaretçi alır.|  
|[GetColumn yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Belirtilen sütun dizininde tablonun belirtilen tablo dizinindeki sütunda bulunan değerlerin için bir işaretçi alır.|  
|[GetColumnInfo yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Belirtilen tabloda belirtilen sütun hakkındaki verileri alır.|  
|[GetGuid yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Belirtilen dizindeki satırdan bir GUID alır.|  
|[GetGuidHeapSize yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|GUID yığın bayt cinsinden boyutu alır.|  
|[GetNextBlob yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Tabloda sonraki BLOB dizinini alır.|  
|[GetNextGuid yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.|  
|[GetNextString yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Sonraki dizenin dizini geçerli bir tablo sütununda alır.|  
|[GetNextUserString yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Sonraki sabit kodlanmış dize geçerli tablo sütununda içeren satırın dizinini alır.|  
|[GetNumTables yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Geçerli kapsamda tablo sayısını alır `IMetaDataTables` örneği.|  
|[GetRow yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Belirtilen satır dizininde belirtilen tablo dizinindeki tablosundaki satır alır.|  
|[GetString yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Dize belirtilen dizindeki geçerli başvuru kapsamda tablo sütunuyla bağlantısı alır.|  
|[GetStringHeapSize yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Dize yığın bayt cinsinden boyutu alır.|  
|[Gettableındex yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Belirtilen belirteç tarafından başvurulan tablo için dizinini alır.|  
|[Gettableınfo yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Ad, satır boyutu, satır sayısı, sütun sayısı ve tablo anahtar sütun dizini belirtilen tablo dizininde alır.|  
|[GetUserString yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Geçerli kapsamdaki dize sütununda belirtilen dizindeki sabit kodlanmış dize alır.|  
|[GetUserStringHeapSize yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Kullanıcı dize yığın bayt cinsinden boyutu alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadatatables2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
