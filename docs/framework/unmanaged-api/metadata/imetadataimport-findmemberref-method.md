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
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175427"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef Yöntemi
Belirtilen <xref:System.Type> ad ve meta veri imzasına sahip üye başvurusu için Üye Ref belirteci alır.  
  
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
 [içinde] Arama için üye başvuruyu içine alan sınıf veya arabirim için TypeRef belirteci. Bu değer `mdTokenNil`ise, arama genel değişken veya genel işlev başvurusu için yapılır.  
  
 `szName`  
 [içinde] Aranacak üye nin adı.  
  
 `pvSigBlob`  
 [içinde] Üye başvurunun ikili meta veri imzasına işaretçi.  
  
 `cbSigBlob`  
 [içinde] `pvSigBlob`Baytboyutu.  
  
 `pmr`  
 [çıkış] Eşleşen ÜyeRef belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Üyeyi çevreleyen sınıfını veya arayüzünü`td`( ),`szName`adını ( ),`pvSigBlob`ve isteğe bağlı olarak imzasını ( ) kullanarak belirtirsiniz.  
  
 İmzalar belirli `FindMemberRef` bir kapsama bağlı olduğundan, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, çevreleyen sınıfı veya değer türünü tanımlayan bir belirteç katıştırabilir. Belirteç, yerel TypeDef tablosuna bir dizindir. Geçerli kapsam bağlamının dışında bir çalışma zamanı imzası oluşturamazsınız ve `FindMemberRef`bu imzayı 'ye giriş olarak kullanamazsınız.  
  
 `FindMemberRef`yalnızca doğrudan sınıf veya arabirimde tanımlanmış üye başvuruları bulur; devralınan üye referansları bulamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
