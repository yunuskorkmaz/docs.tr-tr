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
ms.openlocfilehash: 068014732cee91147edaec29fa0f954a741d8b5c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491673"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef Yöntemi
Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan üye başvurusu Için MemberRef belirtecine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Arama için üye başvurusunu kapsayan sınıf veya arabirim için TypeRef belirteci. Bu değer ise `mdTokenNil` , arama genel bir değişken veya genel işlev başvurusu için yapılır.  
  
 `szName`  
 'ndaki Arama yapılacak üye başvurusunun adı.  
  
 `pvSigBlob`  
 'ndaki Üye başvurusunun ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki Bayt cinsinden boyut `pvSigBlob` .  
  
 `pmr`  
 dışı Eşleşen MemberRef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Üyeyi kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .  
  
 `FindMemberRef`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosunun bir dizinidir. Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı giriş olarak kullanabilirsiniz `FindMemberRef` .  
  
 `FindMemberRef`yalnızca sınıfta veya arabirimde doğrudan tanımlanmış üye başvurularını bulur; devralınan üye başvurularını bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
