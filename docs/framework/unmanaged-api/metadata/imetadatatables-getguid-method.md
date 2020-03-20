---
title: IMetaDataTables::GetGuid Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175284"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid Metodu
Belirtilen dizindeki satırdan bir GUID alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ixGuid`  
 [içinde] GUID almak için satır ın dizin.  
  
 `ppGuid`  
 [çıkış] GUID için bir işaretçi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

  Tutarlı sonuçlar döndürmediği için bu yöntemin kullanılmasını önermiyoruz. GUID tablosu hakkında bilgi için, "Partition II: Metadata Definition and Semantics" başta olmak üzere Ortak Dil Altyapısı (CLI) belgelerine bakın. Dokümantasyon online olarak mevcuttur; bkz. [ECMA C# ve Ortak Dil Altyapı Standartları](../../../standard/components.md#applicable-standards) ve Standart [ECMA-335 - Ortak Dil Altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
