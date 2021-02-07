---
description: ': IMetaDataImport:: Enummethodsemantiği yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9819afb2d7974e9f705c6ff665d3414eade0ab90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728291"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics Yöntemi

Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını sıralar.  
  
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
|`S_OK`|`EnumMethodSemantics` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir olay veya özellik yok. Bu durumda, `pcEventProp` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Birçok ortak dil çalışma zamanı türü  `Changed` , özellikleriyle ilgili özellik olaylarını ve `On` *özellik* `Changed` yöntemlerini tanımlar. Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türü bir <xref:System.Windows.Forms.Control.Font%2A> özelliği, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemini tanımlar. Özellik çağrıları yönteminin ayarlama erişimcisi yöntemi <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.OnFontChanged%2A> , bu da <xref:System.Windows.Forms.Control.FontChanged> olayı oluşturur. `EnumMethodSemantics` <xref:System.Windows.Forms.Control.OnFontChanged%2A> Özelliğine ve olayına başvuru almak için MethodDef kullanarak öğesini çağırın <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.FontChanged> .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
