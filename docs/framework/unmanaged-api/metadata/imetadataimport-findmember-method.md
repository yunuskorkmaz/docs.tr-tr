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
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177276"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember Yöntemi
Belirtilen <xref:System.Type> ad ve meta veri imzasına sahip alan veya yöntem için ÜyeDef belirteci için bir işaretçi alır.  
  
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
 [içinde] Üyenin aranması gereken sınıf veya arabirim için TypeDef belirteci. Bu değer `mdTokenNil`ise, arama genel değişken veya genel işlev için yapılır.  
  
 `szName`  
 [içinde] Aranacak üyenin adı.  
  
 `pvSigBlob`  
 [içinde] Üyenin ikili meta veri imzasına işaretçi.  
  
 `cbSigBlob`  
 [içinde] `pvSigBlob`Baytboyutu.  
  
 `pmb`  
 [çıkış] Eşleşen ÜyeDef belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Üyeyi çevreleyen sınıfını veya arayüzünü`td`( ),`szName`adını ( ),`pvSigBlob`ve isteğe bağlı olarak imzasını ( ) kullanarak belirtirsiniz. Bir sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir. Bu durumda, benzersiz eşleşmeyi bulmak için üyenin imzasını geçirin.  
  
 İmzalar belirli `FindMember` bir kapsama bağlı olduğundan, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, çevreleyen sınıfı veya değer türünü tanımlayan bir belirteç katıştırabilir. Belirteç, yerel TypeDef tablosuna bir dizindir. Geçerli kapsam bağlamının dışında bir çalışma zamanı imzası oluşturamazsınız ve bu imzayı `FindMember`giriş olarak kullanamazsınız.  
  
 `FindMember`yalnızca doğrudan sınıf veya arabirimde tanımlanmış üyeleri bulur; devralınan üyeleri bulamaz.  
  
> [!NOTE]
> `FindMember`yardımcı bir yöntemdir. Bu [iMetaDataImport çağırır::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); bu arama eşleşme bulamazsa, `FindMember` o zaman [iMetaDataImport çağırır::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
