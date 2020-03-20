---
title: IMetaDataImport::EnumMembers Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175492"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers Yöntemi
Belirtilen tipteki üyeleri temsil eden ÜyeDef belirteçlerini oyalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi.  
  
 `cl`  
 [içinde] Üyeleri numaralandırılacak türü temsil eden bir TypeDef belirteci.  
  
 `rMembers`  
 [çıkış] ÜyeDef belirteçlerini tutmak için kullanılan dizi.  
  
 `cMax`  
 [içinde] `rMembers` Dizinin en büyük boyutu.  
  
 `pcTokens`  
 [çıkış] ÜyeDef belirteçlerinin gerçek sayısı `rMembers`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala kaydolacak ÜyeDef belirteçleri yoktur. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sınıf için üye koleksiyonlarını toplarken, `EnumMembers` yalnızca üyeler (alanlar ve yöntemler, ancak özellikler veya olaylar) doğrudan sınıf üzerinde tanımlanan döndürür. **not** Sınıf, devralınan üyeler için bir uygulama sağlasa bile, sınıfın devraldığı hiçbir üyeyi döndürmez. Devralınan üyeleri doğrulamak için, arayan açıkça devralma zincirinde yürümelidir. Devralma zincirinin kurallarının, özgün meta verileri yayan dile veya derleyiciye bağlı olarak değişebileceğini unutmayın.

 Özellikler ve olaylar `EnumMembers`tarafından numaralandırılmez. Bunları sayısallandırmak için [EnumProperties](imetadataimport-enumproperties-method.md) veya [EnumEvents'i](imetadataimport-enumevents-method.md)kullanın.
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
