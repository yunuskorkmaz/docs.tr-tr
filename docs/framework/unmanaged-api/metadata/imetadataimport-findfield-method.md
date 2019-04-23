---
title: IMetaDataImport::FindField Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88cd08b4290739808079bc8ecb713a5c5ea96584
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172568"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField Yöntemi
Bir işaretçi için fieldDef simgesi alınmış bir alan için belirteç alır tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [in] Sınıf veya aramak için alan kapsayan arabirimi TypeDef belirteci. Bu değer ise `mdTokenNil`, genel bir değişken için arama yapılır.  
  
 `szName`  
 [in] Aranacak alan adı.  
  
 `pvSigBlob`  
 [in] Alan ikili meta veri imzası bir işaretçi.  
  
 `cbSigBlob`  
 [in] Bayt cinsinden boyutu `pvSigBlob`.  
  
 `pmb`  
 [out] Eşleşen fieldDef simgesi belirteç için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsayan sınıfı veya arabirimi kullanarak alanı belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).  
  
 İmza geçirilen `FindField` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir. İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir. (Belirteç yerel TypeDef tabloya dizinidir). Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza, giriş olarak kullanmak `FindField`.  
  
 `FindField` sınıf veya arabirim içinde tanımlanmış olan alanlar bulur; devralınan alanları bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
