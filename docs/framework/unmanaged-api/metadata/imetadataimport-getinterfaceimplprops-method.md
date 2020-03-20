---
title: IMetaDataImport::GetInterfaceImplProps Yöntemi
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175388"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps Yöntemi
Belirtilen yöntemi uygulayanlar ve bu yöntemi <xref:System.Type> bildiren arabirim için meta veri belirteçleri için bir işaretçi alır.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iiImpl`  
 [içinde] Sınıf ve arabirim belirteçlerini döndürme yöntemini temsil eden meta veri belirteci.  
  
 `pClass`  
 [çıkış] Yöntemi uygulayan sınıfı temsil eden meta veri belirteci.  
  
 `ptkIface`  
 [çıkış] Uygulanan yöntemi tanımlayan arabirimi temsil eden meta veri belirteci.  

## <a name="remarks"></a>Açıklamalar

 `iImpl` [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) yöntemini arayarak değer elde elabilirsiniz.

 Örneğin, bir sınıfın 0x02000007 `mdTypeDef` belirteç değerine sahip olduğunu ve türleri belirteçleri olan üç arabirim uyguladığını varsayalım:

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x020001C (TypeDef)

Kavramsal olarak, bu bilgiler bir arayüz uygulama tablosunda şu şekilde depolanır:

| Satır numarası | Sınıf belirteci | Arabirim belirteci |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Geri çağırma, belirteç 4 bayt lık bir değerdir:

- Alt 3 bayt satır numarasını veya RID'yi tutar.
- Üst bayt belirteç türünü tutar – `mdtInterfaceImpl`0x09 için .

`GetInterfaceImplProps`satırda tutulan ve bağımsız değişkende belirteç verdiğiniz bilgileri döndürür. `iImpl`
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
