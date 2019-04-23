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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abbd35fe390cc09951b762a5fd671d2d34a57c6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177898"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef Yöntemi
Diğer bir deyişle MemberRef belirteci üyesi için bir işaretçiye başvuru alır içine tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta verileri imza sahip.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Sınıf veya üye başvurusu aranacak kapsayan arabirimi TypeRef belirteci. Bu değer ise `mdTokenNil`, genel değişken veya işlev genel başvurusu için arama yapılır.  
  
 `szName`  
 [in] Aranacak üyesi başvuru adı.  
  
 `pvSigBlob`  
 [in] Üye başvurusu ikili meta veri imzası bir işaretçi.  
  
 `cbSigBlob`  
 [in] Bayt cinsinden boyutu `pvSigBlob`.  
  
 `pmr`  
 [out] Eşleşen MemberRef belirteç için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsayan sınıfı veya arabirimi kullanılarak üyesi belirtin (`td`), adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).  
  
 İmza geçirilen `FindMemberRef` imzaları belirli bir kapsama bağlı oldukları için geçerli kapsamda oluşturulan gerekir. İmza kapsayan sınıf veya değer türü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosuna bir dizindir. Geçerli kapsam bağlamında dışında bir çalışma zamanı imza oluşturun ve bu imza, giriş olarak kullanmak `FindMemberRef`.  
  
 `FindMemberRef` sınıf veya arabirim içinde tanımlanmış olan üye başvuruları bulur; devralınan üye başvuruları bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
