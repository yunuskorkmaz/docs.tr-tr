---
title: IMetaDataImport::FindMember Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: 7a46fa5319a1badc0cf28dcdbf535a6ed017c9c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437920"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember Yöntemi
Belirtilen <xref:System.Type> alınmış ve belirtilen ad ve meta veri imzasına sahip olan alan veya yöntem için MemberDef belirtecine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki Aranacak üyeyi kapsayan sınıf veya arabirim için TypeDef belirteci. Bu değer `mdTokenNil`ise, arama genel değişken veya genel işlev için yapılır.  
  
 `szName`  
 'ndaki Aranacak üyenin adı.  
  
 `pvSigBlob`  
 'ndaki Üyenin ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki `pvSigBlob`bayt cinsinden boyutu.  
  
 `pmb`  
 dışı Eşleşen MemberDef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Üyeyi kapsayan sınıfını veya arabirimini (`td`), adını (`szName`) ve isteğe bağlı olarak imzasını (`pvSigBlob`) kullanarak belirtirsiniz. Bir sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir. Bu durumda, benzersiz eşleşmeyi bulmak için üyenin imzasını geçirin.  
  
 İmzaların belirli bir kapsama bağlandığı için `FindMember` geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosunun bir dizinidir. Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı `FindMember`giriş olarak kullanabilirsiniz.  
  
 `FindMember` yalnızca doğrudan sınıfta veya arabirimde tanımlanmış olan üyeleri bulur; devralınan üyeleri bulamaz.  
  
> [!NOTE]
> `FindMember` bir yardımcı yöntemidir. [IMetaDataImport:: FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); öğesini çağırır Bu çağrı bir eşleşme bulamazsa, `FindMember` sonra [IMetaDataImport:: FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)' ı çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
