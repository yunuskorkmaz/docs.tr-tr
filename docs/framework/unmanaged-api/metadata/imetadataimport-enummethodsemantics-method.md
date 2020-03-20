---
title: IMetaDataImport::EnumMethodSemantics Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175466"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics Yöntemi
Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını günceller.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi. Bu yöntemin ilk araması için NULL olmalıdır.  
  
 `mb`  
 [içinde] Numaralandırmakapsamını sınırlayan bir MethodDef belirteci.  
  
 `rEventProp`  
 [çıkış] Olayları veya özellikleri depolamak için kullanılan dizi.  
  
 `cMax`  
 [içinde] `rEventProp` Dizinin en büyük boyutu.  
  
 `pcEventProp`  
 [çıkış] Döndürülen olay veya özellik `rEventProp`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala'da olay veya özellik yoktur. Bu durumda, `pcEventProp` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Birçok yaygın dil çalışma *Property* `Changed` zamanı `On`türleri, özellikleriyle ilgili Özellik olayları ve *Özellik* `Changed` yöntemlerini tanımlar. Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> tür bir <xref:System.Windows.Forms.Control.Font%2A> özellik, bir <xref:System.Windows.Forms.Control.FontChanged> olay ve <xref:System.Windows.Forms.Control.OnFontChanged%2A> bir yöntem tanımlar. Özellik arama <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.OnFontChanged%2A> yönteminin ayarlı erişimci yöntemi, <xref:System.Windows.Forms.Control.FontChanged> sırayla olayı yükseltir. Özellik ve `EnumMethodSemantics` <xref:System.Windows.Forms.Control.FontChanged> olay başvuruları <xref:System.Windows.Forms.Control.OnFontChanged%2A> almak için MethodDef kullanarak aramak istiyorsunuz. <xref:System.Windows.Forms.Control.Font%2A>  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
