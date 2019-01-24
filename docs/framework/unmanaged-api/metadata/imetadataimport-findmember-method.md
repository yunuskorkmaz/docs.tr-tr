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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 267a36fbbdf48472bc35581ce98af5cd7a9cef9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550376"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember Yöntemi
Bir işaretçi için MemberDef alan veya alınmış yöntemi için belirteç alır tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Sınıf veya üye aranacak kapsayan arabirimi TypeDef belirteci. Bu değer ise `mdTokenNil`, bir genel değişken veya işlev genel arama yapılır.  
  
 `szName`  
 [in] Aranacak üyesinin adı.  
  
 `pvSigBlob`  
 [in] İkili meta veri imzası üyenin bir işaretçisi.  
  
 `cbSigBlob`  
 [in] Bayt cinsinden boyutu `pvSigBlob`.  
  
 `pmb`  
 [out] Eşleşen MemberDef belirteç için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsayan sınıfı veya arabirimi kullanılarak üyesi belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`). Sınıfta veya arabirimde aynı ada sahip birden çok üye olabilir. Bu durumda, benzersiz bir eşleşme bulmak için üyenin imzasını geçirin.  
  
 İmza geçirilen `FindMember` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir. İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosuna bir dizindir. Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza olarak giriş için giriş kullanmasına `FindMember`.  
  
 `FindMember` sınıf veya arabirim içinde tanımlanmış üyeler bulur; devralınan üyeleri bulmaz.  
  
> [!NOTE]
>  `FindMember` bir yardımcı yöntemdir. Çağrı [Imetadataımport::findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); bu çağrı bir eşleşme bulamazsa `FindMember` sonra çağıran [Imetadataımport::findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
