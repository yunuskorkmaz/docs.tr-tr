---
title: IMetaDataImport::GetNestedClassProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 82cf5e14520f0e677c2d274cf013d8a0020e8fa2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503542"
---
# <a name="imetadataimportgetnestedclassprops-method"></a>IMetaDataImport::GetNestedClassProps Metodu
Belirtilen iç içe türün üst öğesi için TypeDef belirtecini alır <xref:System.Type> .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tdNestedClass`  
 'ndaki <xref:System.Type>İçin üst sınıf belirtecini döndürmek üzere öğesini temsil eden bir typedef belirteci.  
  
 `ptdEnclosingClass`  
 dışı <xref:System.Type>İçinde iç içe olan Için typedef belirtecine yönelik bir işaretçi `tdNestedClass` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
