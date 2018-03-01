---
title: "IMetaDataImport::FindMethod Yöntemi"
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
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e59cc440ba004545c31d6b25d36cca4fdfb58899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod Yöntemi
Bir işaretçi MethodDef içine yöntemi için belirteç alır belirtilen tarafından <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] `mdTypeDef` Aramak için üye kapsayan türü için (bir sınıf veya arabirim) belirteci. Bu değer ise `mdTokenNil`, genel bir işlev için arama yapılır.  
  
 `szName`  
 [in] Aranacak yöntem adı.  
  
 `pvSigBlob`  
 [in] Yönteminin ikili meta verileri imza için bir işaretçi.  
  
 `cbSigBlob`  
 [in] Bayt cinsinden boyutu `pvSigBlob`.  
  
 `pmb`  
 [out] Eşleşen MethodDef belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsayan sınıf ya da arabirimi kullanarak yöntemini belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`). Bir sınıf ya da arabirimi aynı ada sahip birden çok yöntem olabilir. Bu durumda, benzersiz bir eşleşme bulmak için yöntemin imzası geçirin.  
  
 İmza geçirilen `FindMethod` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır. İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir. Belirteç yerel TypeDef tabloya dizinidir. Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve bu imza olarak giriş için giriş kullanmasına `FindMethod`.  
  
 `FindMethod`doğrudan sınıfta veya arabirimde tanımlanan yöntemler bulur; devralınan yöntemleri bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.MethodInfo>  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
