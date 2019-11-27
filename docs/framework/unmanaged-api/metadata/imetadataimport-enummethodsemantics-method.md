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
ms.openlocfilehash: ff6932b6040a19e0ccda2f8d2140fa131cdd9224
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450069"
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
 'ndaki `rEventProp` dizisinin en büyük boyutu.  
  
 `pcEventProp`  
 dışı `rEventProp`döndürülen olay veya özellik sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir olay veya özellik yok. Bu durumda `pcEventProp` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Birçok ortak dil çalışma zamanı türü *özellik*`Changed` olaylarını ve özellikleriyle Ilgili `On`*özelliği*`Changed` yöntemlerini tanımlar. Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türü bir <xref:System.Windows.Forms.Control.Font%2A> özelliğini, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemini tanımlar. <xref:System.Windows.Forms.Control.Font%2A> özelliğinin set erişimcisi yöntemi <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemini çağırır, bu da <xref:System.Windows.Forms.Control.FontChanged> olayını oluşturur. <xref:System.Windows.Forms.Control.Font%2A> özelliğine ve <xref:System.Windows.Forms.Control.FontChanged> olayına başvuru almak için <xref:System.Windows.Forms.Control.OnFontChanged%2A> MethodDef kullanarak `EnumMethodSemantics` çağırırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
