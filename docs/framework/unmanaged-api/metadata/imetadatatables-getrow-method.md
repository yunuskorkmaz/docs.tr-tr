---
title: IMetaDataTables::GetRow Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177113"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow Yöntemi
Belirtilen satır dizinindeki satırı, belirtilen tablo dizinindeki tabloda alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ixTbl`  
 [içinde] Satırın alınacağı tablonun dizini.  
  
 `rid`  
 [içinde] Almak için satır ın dizini.  
  
 `ppRow`  
 [çıkış] Satıra işaretçi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

  Tutarlı sonuçlar döndürmediği için bu yöntemin kullanılmasını önermiyoruz. GUID tablosu hakkında bilgi için, "Partition II: Metadata Definition and Semantics" başta olmak üzere Ortak Dil Altyapısı (CLI) belgelerine bakın. Dokümantasyon online olarak mevcuttur; bkz. [ECMA C# ve Ortak Dil Altyapı Standartları](../../../standard/components.md#applicable-standards) ve Standart [ECMA-335 - Ortak Dil Altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
