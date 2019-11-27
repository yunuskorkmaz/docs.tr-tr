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
ms.openlocfilehash: 842d6c0deb90bc45cb59454fb30fcc3544d742f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437944"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField Yöntemi
Belirtilen <xref:System.Type> içine alınmış ve belirtilen ad ve meta veri imzasına sahip olan alan için FieldDef belirtecine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Aranacak alanı kapsayan sınıf veya arabirim için TypeDef belirteci. Bu değer `mdTokenNil`, genel bir değişken için arama yapılır.  
  
 `szName`  
 'ndaki Aranacak alanın adı.  
  
 `pvSigBlob`  
 'ndaki Alanın ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki `pvSigBlob`bayt cinsinden boyutu.  
  
 `pmb`  
 dışı Eşleşen FieldDef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Alanı kapsayan sınıfını veya arabirimini (`td`), adını (`szName`) ve isteğe bağlı olarak imzasını (`pvSigBlob`) kullanarak belirtirsiniz.  
  
 İmzaların belirli bir kapsama bağlandığı için `FindField` geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. (Belirteç yerel TypeDef tablosunun bir dizinidir). Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı `FindField`giriş olarak kullanabilirsiniz.  
  
 `FindField` yalnızca doğrudan sınıfta veya arabirimde tanımlanan alanları bulur; devralınan alanları bulamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
