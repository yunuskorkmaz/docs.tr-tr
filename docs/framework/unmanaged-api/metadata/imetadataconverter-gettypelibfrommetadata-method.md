---
title: IMetaDataConverter::GetTypeLibFromMetaData Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: ef573eb9a572c27e685289b2740a55e898be2093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177627"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a>IMetaDataConverter::GetTypeLibFromMetaData Yöntemi
Belirtilen kitaplık `ITypeLib` ve modül adlarına sahip tür kitaplığını temsil eden bir örneğin işaretçisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `strModule`  
 [içinde] Tür kitaplığı modülünün adı.  
  
 `strTlbName`  
 [içinde] Tür kitaplığın adı.  
  
 `ppITL`  
 [çıkış] Tür kitaplığını temsil eden `ITypeLib` örneğin adresini alan bir konuma işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataConverter Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
