---
title: IMetaDataImport::FindMemberRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 59512cc1c1b280d7fe6deb2f9d721ad53547e356
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437962"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef Yöntemi
Belirtilen <xref:System.Type> içine alınmış ve belirtilen ad ve meta veri imzasına sahip olan üye başvurusunun MemberRef belirtecine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki Arama için üye başvurusunu kapsayan sınıf veya arabirim için TypeRef belirteci. Bu değer `mdTokenNil`, arama genel bir değişken veya genel işlev başvurusu için yapılır.  
  
 `szName`  
 'ndaki Arama yapılacak üye başvurusunun adı.  
  
 `pvSigBlob`  
 'ndaki Üye başvurusunun ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki `pvSigBlob`bayt cinsinden boyutu.  
  
 `pmr`  
 dışı Eşleşen MemberRef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Üyeyi kapsayan sınıfını veya arabirimini (`td`), adını (`szName`) ve isteğe bağlı olarak imzasını (`pvSigBlob`) kullanarak belirtirsiniz.  
  
 İmzaların belirli bir kapsama bağlandığı için `FindMemberRef` geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosunun bir dizinidir. Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı `FindMemberRef`giriş olarak kullanabilirsiniz.  
  
 `FindMemberRef` yalnızca sınıfta veya arabirimde doğrudan tanımlanmış üye başvurularını bulur; devralınan üye başvurularını bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
