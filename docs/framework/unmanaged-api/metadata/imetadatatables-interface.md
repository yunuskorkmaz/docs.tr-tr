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
ms.openlocfilehash: 073e73f082416308b893974471e39cbf5243d01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708861"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables Arabirimi

Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBlob Yöntemi](imetadatatables-getblob-method.md)|Belirtilen sütun dizininde ikili büyük nesne (BLOB) için bir işaretçi alır.|  
|[GetBlobHeapSize Yöntemi](imetadatatables-getblobheapsize-method.md)|BLOB yığınının boyutunu bayt cinsinden alır.|  
|[GetCodedTokenInfo Yöntemi](imetadatatables-getcodedtokeninfo-method.md)|Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.|  
|[GetColumn Yöntemi](imetadatatables-getcolumn-method.md)|Belirtilen tablo dizinindeki tabloda belirtilen sütun dizinindeki sütunda bulunan değerlere yönelik bir işaretçi alır.|  
|[GetColumnInfo Yöntemi](imetadatatables-getcolumninfo-method.md)|Belirtilen tabloda belirtilen sütunla ilgili verileri alır.|  
|[GetGuid Yöntemi](imetadatatables-getguid-method.md)|Belirtilen dizindeki satırdan bir GUID alır.|  
|[GetGuidHeapSize Yöntemi](imetadatatables-getguidheapsize-method.md)|GUID yığınının boyutunu bayt cinsinden alır.|  
|[GetNextBlob Yöntemi](imetadatatables-getnextblob-method.md)|Tablodaki sonraki BLOBUN dizinini alır.|  
|[GetNextGuid Yöntemi](imetadatatables-getnextguid-method.md)|Geçerli tablo sütunundaki sonraki GUID değerinin dizinini alır.|  
|[GetNextString Yöntemi](imetadatatables-getnextstring-method.md)|Geçerli tablo sütunundaki sonraki dizenin dizinini alır.|  
|[GetNextUserString Yöntemi](imetadatatables-getnextuserstring-method.md)|Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.|  
|[GetNumTables Yöntemi](imetadatatables-getnumtables-method.md)|Geçerli örnek kapsamındaki tablo sayısını alır `IMetaDataTables` .|  
|[GetRow Yöntemi](imetadatatables-getrow-method.md)|Belirtilen tablo dizinindeki tabloda belirtilen satır dizinindeki satırı alır.|  
|[GetString Yöntemi](imetadatatables-getstring-method.md)|Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.|  
|[GetStringHeapSize Yöntemi](imetadatatables-getstringheapsize-method.md)|Dize yığınının boyutunu bayt cinsinden alır.|  
|[GetTableIndex Yöntemi](imetadatatables-gettableindex-method.md)|Belirtilen belirteç tarafından başvurulan tablonun dizinini alır.|  
|[GetTableInfo Yöntemi](imetadatatables-gettableinfo-method.md)|Belirtilen tablo dizinindeki tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.|  
|[GetUserString Yöntemi](imetadatatables-getuserstring-method.md)|Geçerli kapsamdaki dize sütununda belirtilen dizinde sabit kodlanmış dizeyi alır.|  
|[GetUserStringHeapSize Yöntemi](imetadatatables-getuserstringheapsize-method.md)|Kullanıcı dizesi yığınının bayt cinsinden boyutunu alır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
