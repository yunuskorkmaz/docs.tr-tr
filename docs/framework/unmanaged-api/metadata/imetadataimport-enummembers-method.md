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
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492065"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers Yöntemi
Belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [in, out] Numaralandırıcı için bir işaretçi.  
  
 `cl`  
 'ndaki Üyeleri numaralandırılmış olan türü temsil eden bir TypeDef belirteci.  
  
 `rMembers`  
 dışı MemberDef belirteçlerini tutmak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rMembers` .  
  
 `pcTokens`  
 dışı İçinde döndürülen MemberDef belirteçlerinin gerçek sayısı `rMembers` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak MemberDef belirteçleri yok. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sınıf için üye koleksiyonları numaralandırılırken, `EnumMembers` doğrudan sınıfında tanımlanmış üyeleri (alanlar ve Yöntemler, ancak Özellikler veya olaylar **değil** ) döndürür. Sınıf, devralınan Üyeler için bir uygulama sağladığından bile, sınıfın devraldığı herhangi bir üye döndürmez. Devralınan üyeleri listelemek için çağıran, devralma zincirini açıkça yürümelidir. Devralma zincirinin kurallarının, özgün meta verileri oluşturan dile veya derleyiciye göre değişebileceğini unutmayın.

 Özellikler ve olaylar tarafından numaralandırılmıyor `EnumMembers` . Bunları listelemek için, [EnumProperties](imetadataimport-enumproperties-method.md) veya [trmevents](imetadataimport-enumevents-method.md)kullanın.
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
