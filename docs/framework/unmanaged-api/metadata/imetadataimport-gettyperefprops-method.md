---
description: ': IMetaDataImport:: GetTypeRefProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetTypeRefProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 8d4741ca2d04aaa4af48fee2cf6485de3403a525
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789131"
---
# <a name="imetadataimportgettyperefprops-method"></a>IMetaDataImport::GetTypeRefProps Metodu

Belirtilen TypeRef belirtecinin başvurduğu ile ilişkili meta verileri alır <xref:System.Type> .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `tr`  
 'ndaki Meta verilerini döndürecek türü temsil eden TypeRef belirteci.  
  
 `ptkResolutionScope`  
 dışı Başvurunun yapıldığı kapsama yönelik bir işaretçi. Bu değer bir AssemblyRef veya ModuleRef belirtecidir.  
  
 `szName`  
 dışı Tür adını içeren bir arabellek.  
  
 `cchName`  
 'ndaki Geniş karakterdeki istenen boyut `szName` .  
  
 `pchName`  
 dışı Geniş karakter olarak döndürülen boyut `szName` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
