---
title: ICeeGen::AddSectionReloc Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176116"
---
# <a name="iceegenaddsectionreloc-method"></a>ICeeGen::AddSectionReloc Yöntemi
Kod tabanına bir .reloc yönergesi ekler.  
  
 Bu yöntem eskidir ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `section`  
 [içinde] .reloc yönergesi ekleyeceğiniz bellek içi kod bölümü.  
  
 `offset`  
 [içinde] Bölümün mahsup.  
  
 `relativeTo`  
 [içinde] Başvurulan `offset` bölüm.  
  
 `relocType`  
 [içinde] [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) değerlerinden biri, eklemek için .reloc yönergesi türünü gösteren.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
