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
ms.openlocfilehash: 28aa8313e7ba0c071187d0f1f6d78431b16fc005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164807"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod Yöntemi
Bir işaretçi için MethodDef alınmış yöntemi için belirteç alır tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [in] `mdTypeDef` Belirteci aranacak üye kapsayan türü için (bir sınıf veya arabirim). Bu değer ise `mdTokenNil`, genel bir işlev için arama yapılır.  
  
 `szName`  
 [in] Aranacak yöntemin adı.  
  
 `pvSigBlob`  
 [in] İkili meta veri imzası yöntem bir işaretçi.  
  
 `cbSigBlob`  
 [in] Bayt cinsinden boyutu `pvSigBlob`.  
  
 `pmb`  
 [out] Eşleşen MethodDef belirteç için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsayan sınıfı veya arabirimi kullanarak yöntemini belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`). Bir sınıfı veya arabirimi aynı ada sahip birden çok yöntem olabilir. Bu durumda, benzersiz bir eşleşme bulmak için yöntemin imzasını geçirin.  
  
 İmza geçirilen `FindMethod` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir. İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosuna bir dizindir. Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza olarak giriş için giriş kullanmasına `FindMethod`.  
  
 `FindMethod` sınıf veya arabirim içinde tanımlanmış olan yöntemleri bulur; devralınan yöntemleri bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
