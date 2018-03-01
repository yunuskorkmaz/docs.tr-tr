---
title: "IMetaDataAssemblyEmit::DefineExportedType Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType Yöntemi
Oluşturur bir `ExportedType` belirtilen türü dışarı ve ilişkili meta veri simgesi döndürür için meta verileri içeren yapısı.  
  
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
 [in] Dışa aktarılacak türünün adı. 1.1 ortak dil çalışma zamanı sürümü, dışarı aktarılan türünün adı verilen adı tam olarak eşleşmelidir için `TypeDef` türü için.  
  
 `tkImplementation`  
 [in] Burada verilen tür uygulanan belirten bir simge. İlişkili anlamlarını ve geçerli değerler şunlardır:  
  
-   `mdFile`Bu derleme içinde farklı bir dosya türü uygulanır.  
  
-   `mdAssemblyRef`Türü farklı bir derlemede uygulanır.  
  
-   `mdExportedTYpe`Türü, başka bir türü içinde yer alıyor.  
  
-   `mdFileNil`Türü bildirimi aynı dosyasındaki ve iç içe geçmiş bir tür değil.  
  
 `tkTypeDef`  
 [in] Bir belirteç meta verilerinin verilecek türünü belirtir. Bu değer girildiğini `TypeDef` türü uygulayan ve yalnızca bu dosya bu derlemede olduğunda geçerlidir dosya tablosunda.  
  
 `dwExportedTypeFlags`  
 [in] Bit düzeyinde bileşimini [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) dışarı aktarılan tür için özellik ayarları tanımlayan numaralandırma değerleri.  
  
 `pmdct`  
 [out] Dışarı aktarılan türünü gösteren döndürülen meta veri simgesi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ExportedType` meta veri yapısı, bu derlemesi tarafından gösterilir ve bildirim içeren farklı bir modüldeki uygulanan her tür için tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
