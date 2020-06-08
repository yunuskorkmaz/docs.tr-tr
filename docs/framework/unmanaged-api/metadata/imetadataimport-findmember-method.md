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
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503685"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember Yöntemi
Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan alan veya yöntem Için MemberDef belirtecine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Aranacak üyeyi kapsayan sınıf veya arabirim için TypeDef belirteci. Bu değer ise `mdTokenNil` , arama genel değişken veya genel işlev için yapılır.  
  
 `szName`  
 'ndaki Aranacak üyenin adı.  
  
 `pvSigBlob`  
 'ndaki Üyenin ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki Bayt cinsinden boyut `pvSigBlob` .  
  
 `pmb`  
 dışı Eşleşen MemberDef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Üyeyi kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` . Bir sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir. Bu durumda, benzersiz eşleşmeyi bulmak için üyenin imzasını geçirin.  
  
 `FindMember`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosunun bir dizinidir. Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı girişi yapılacak girdi olarak kullanabilirsiniz `FindMember` .  
  
 `FindMember`yalnızca sınıfta veya arabirimde doğrudan tanımlanmış olan üyeleri bulur; devralınan üyeleri bulamaz.  
  
> [!NOTE]
> `FindMember`bir yardımcı yöntemidir. [IMetaDataImport:: FindMethod](imetadataimport-findmethod-method.md); öğesini çağırır Bu çağrı bir eşleşme bulamazsa, `FindMember` [IMetaDataImport:: FindField](imetadataimport-findfield-method.md)' ı çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
