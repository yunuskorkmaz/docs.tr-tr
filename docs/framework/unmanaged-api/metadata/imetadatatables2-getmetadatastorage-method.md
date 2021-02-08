---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables2:: GetMetaDataStorage Yöntemi'
title: IMetaDataTables2::GetMetaDataStorage Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: df6bbc69be05986dc6d4f143cec7ec09a2d78ee5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799258"
---
# <a name="imetadatatables2getmetadatastorage-method"></a>IMetaDataTables2::GetMetaDataStorage Metodu

Belirtilen bölümde depolanan meta verilerin boyutunu ve içeriğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppvMd`  
 [in, out] Meta veri bölümüne yönelik bir işaretçi.  
  
 `pcbMd`  
 dışı Meta veri akışının boyutu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
