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
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437890"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod Yöntemi
Belirtilen <xref:System.Type> içine alınmış ve belirtilen ad ve meta veri imzasına sahip olan metodun MethodDef belirtecine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Aramak için üyeyi kapsayan türün `mdTypeDef` belirteci (bir sınıf veya arabirim). Bu değer `mdTokenNil`, genel bir işlev için arama yapılır.  
  
 `szName`  
 'ndaki Aranacak yöntemin adı.  
  
 `pvSigBlob`  
 'ndaki Metodun ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki `pvSigBlob`bayt cinsinden boyutu.  
  
 `pmb`  
 dışı Eşleşen MethodDef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi kapsayan sınıfını veya arabirimini (`td`), adını (`szName`) ve isteğe bağlı olarak imzasını (`pvSigBlob`) kullanarak belirtirsiniz. Bir sınıfta veya arabirimde aynı ada sahip birden çok yöntem olabilir. Bu durumda, benzersiz eşleşmeyi bulmak için yöntemin imzasını geçirin.  
  
 İmzaların belirli bir kapsama bağlandığı için `FindMethod` geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosunun bir dizinidir. Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı `FindMethod`giriş olarak kullanabilirsiniz.  
  
 `FindMethod` yalnızca doğrudan sınıfta veya arabirimde tanımlanmış yöntemleri bulur; devralınan yöntemleri bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
