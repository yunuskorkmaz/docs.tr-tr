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
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437544"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps Yöntemi
Belirtilen yöntemi uygulayan <xref:System.Type> için meta veri belirteçleri ve bu yöntemi bildiren arabirim için bir işaretçi alır.
  
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
 'ndaki İçin sınıfı ve arabirim belirteçlerini döndürme yöntemini temsil eden meta veri belirteci.  
  
 `pClass`  
 dışı Yöntemi uygulayan sınıfı temsil eden meta veri belirteci.  
  
 `ptkIface`  
 dışı Uygulanan yöntemi tanımlayan arabirimi temsil eden meta veri belirteci.  

## <a name="remarks"></a>Açıklamalar

 [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) yöntemini çağırarak `iImpl` değerini elde edersiniz.
 
 Örneğin, bir sınıfın 0x02000007 `mdTypeDef` belirteç değerine sahip olduğunu ve türleri belirteçleri olan üç arabirim uyguladığını varsayalım: 

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
- Üst bayt `mdtInterfaceImpl`için 0x09 belirteç türünü tutar.

`GetInterfaceImplProps`, belirtecini `iImpl` bağımsız değişkeninde sağladığınız satırda tutulan bilgileri döndürür. 
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
