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
ms.openlocfilehash: 213cbd955e3d47a49abde579a54af48641e225ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491933"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics Yöntemi
Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını sıralar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [in, out] Numaralandırıcı için bir işaretçi. Bu yöntemin ilk çağrısı için bu NULL olmalıdır.  
  
 `mb`  
 'ndaki Sabit listesinin kapsamını sınırlayan bir MethodDef belirteci.  
  
 `rEventProp`  
 dışı Olayları veya özellikleri depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rEventProp` .  
  
 `pcEventProp`  
 dışı İçinde döndürülen olay veya özellik sayısı `rEventProp` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir olay veya özellik yok. Bu durumda, `pcEventProp` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Birçok ortak dil çalışma zamanı türü *Property* `Changed` , özellikleriyle ilgili özellik olaylarını ve `On` *özellik* `Changed` yöntemlerini tanımlar. Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türü bir <xref:System.Windows.Forms.Control.Font%2A> özelliği, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemini tanımlar. Özellik çağrıları yönteminin ayarlama erişimcisi yöntemi <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.OnFontChanged%2A> , bu da <xref:System.Windows.Forms.Control.FontChanged> olayı oluşturur. `EnumMethodSemantics` <xref:System.Windows.Forms.Control.OnFontChanged%2A> Özelliğine ve olayına başvuru almak için MethodDef kullanarak öğesini çağırın <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.FontChanged> .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
