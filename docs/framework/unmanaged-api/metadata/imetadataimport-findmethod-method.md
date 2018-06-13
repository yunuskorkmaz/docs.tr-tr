---
title: IMetaDataImport::FindMethod Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b68d4e3d51fdb50290319de804a78c1a78a07a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447394"
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
  
 `FindMethod` doğrudan sınıfta veya arabirimde tanımlanan yöntemler bulur; devralınan yöntemleri bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.MethodInfo>  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
