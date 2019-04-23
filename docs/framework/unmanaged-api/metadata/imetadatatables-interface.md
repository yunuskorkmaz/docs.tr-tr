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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131423"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables Arabirimi
Tablo meta veri bilgilerini alma ve depolama için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBlob Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Bir işaretçi ikili büyük nesne (BLOB) için belirtilen sütun dizini alır.|  
|[GetBlobHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|BLOB yığın bayt cinsinden boyutunu alır.|  
|[GetCodedTokenInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Belirteçlerin belirtilen satır dizini ile ilişkili bir diziye bir işaretçi alır.|  
|[GetColumn Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Belirtilen tablo dizini altındaki tabloda belirtilen sütun dizinindeki sütunda bulunan değerleri için bir işaretçi alır.|  
|[GetColumnInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Belirtilen tabloda belirtilen sütuna ilişkin verileri alır.|  
|[GetGuid Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Belirtilen dizindeki satırdaki bir GUID alır.|  
|[GetGuidHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|GUID yığın bayt cinsinden boyutunu alır.|  
|[GetNextBlob Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Sonraki blob dizin tablosunda alır.|  
|[GetNextGuid Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.|  
|[GetNextString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Geçerli bir tablo sütununda sonraki dize dizinini alır.|  
|[GetNextUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Sonraki sabit kodlanmış dize geçerli bir tablo sütunu içeren satırı dizinini alır.|  
|[GetNumTables Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Tablo sayısı geçerli kapsamda alır `IMetaDataTables` örneği.|  
|[GetRow Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Belirtilen tablo dizini altındaki tabloda belirtilen satır dizinindeki bir satır alır.|  
|[GetString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Dize, geçerli başvuru kapsamda tablo sütunuyla bağlantısı belirtilen dizindeki alır.|  
|[GetStringHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Dize yığın bayt cinsinden boyutunu alır.|  
|[GetTableIndex Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Belirtilen belirteç tarafından başvurulan tablo için dizinini alır.|  
|[GetTableInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Belirtilen tablo dizin adı, satır boyutu, satır sayısı, sütun sayısı ve tablonun anahtar sütunu dizini alır.|  
|[GetUserString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Geçerli kapsamdaki dize sütununda belirtilen dizindeki sabit kodlanmış bir dize alır.|  
|[GetUserStringHeapSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Kullanıcı dize yığın bayt cinsinden boyutunu alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
