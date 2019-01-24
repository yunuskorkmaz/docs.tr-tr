---
title: IMetaDataAssemblyEmit::DefineExportedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 071466858c79fdb74d9055fed09990cdb02a88b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624356"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType Yöntemi
Oluşturur bir `ExportedType` yapısı meta verilerini içeren, belirtilen dışarı türü ve ilişkili meta veri belirteci döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szName`  
 [in] Dışa aktarılacak tür adı. Sürüm 1.1 ortak dil çalışma zamanının dışarı aktarılan tür adı verilen ad tam eşleşmelidir `TypeDef` türü.  
  
 `tkImplementation`  
 [in] Dışarı aktarılan tür burada uygulanan belirten bir belirteç. Geçerli değerler ve bunların ilişkili anlamları vardır:  
  
-   `mdFile` Bu derleme içinde farklı bir dosya türü uygulanır.  
  
-   `mdAssemblyRef` Türü farklı bir derlemede uygulanır.  
  
-   `mdExportedTYpe` Tür, başka bir tür içinde yer alıyor.  
  
-   `mdFileNil` Türü, bildirim olarak aynı dosya ve iç içe geçmiş bir tür değil.  
  
 `tkTypeDef`  
 [in] Bir belirteci meta veri dışarı aktarılmasına izin türünü belirtir. İçinde bu değer girilir `TypeDef` tablo dosyanızda türün uyguladığı ve yalnızca bu dosya bu derlemede olduğunda geçerlidir.  
  
 `dwExportedTypeFlags`  
 [in] Bitsel bir birleşimi [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) özellik ayarları dışarı aktarılan türü tanımlayan sabit listesi değerleri.  
  
 `pmdct`  
 [out] Dışarı aktarılan tür gösteren döndürülen meta veri belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ExportedType` meta veri yapısı, bu derleme tarafından kullanıma sunulan ve bildirimini içeren farklı bir modül içinde uygulanan her türü için tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
