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
ms.openlocfilehash: 1c9d9647084aa729817eeeb17ee3f5cd320c0d29
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491255"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps Yöntemi
Belirtilen yöntemi uygulayan için meta veri belirteçlerine <xref:System.Type> ve bu yöntemi bildiren arabirime yönelik bir işaretçi alır.
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iiImpl`  
 'ndaki İçin sınıfı ve arabirim belirteçlerini döndürme yöntemini temsil eden meta veri belirteci.  
  
 `pClass`  
 dışı Yöntemi uygulayan sınıfı temsil eden meta veri belirteci.  
  
 `ptkIface`  
 dışı Uygulanan yöntemi tanımlayan arabirimi temsil eden meta veri belirteci.  

## <a name="remarks"></a>Açıklamalar

 `iImpl` [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) metodunu çağırarak değerini elde edersiniz.

 Örneğin, bir sınıfın `mdTypeDef` 0x02000007 belirteç değerine sahip olduğunu ve türleri belirteçleri olan üç arabirim uyguladığını varsayalım:

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Kavramsal olarak, bu bilgiler bir arabirim uygulama tablosunda şu şekilde depolanır:

| Satır numarası | Sınıf belirteci | Arabirim belirteci |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Geri çağır, belirteç 4 baytlık bir değerdir:

- Alt 3 bayt satır numarasını veya RID 'yi tutar.
- Üst bayt, için – 0x09 belirteç türünü tutar `mdtInterfaceImpl` .

`GetInterfaceImplProps`bağımsız değişkeninde sağladığınız satırı içeren satırda tutulan bilgileri döndürür `iImpl` .
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
