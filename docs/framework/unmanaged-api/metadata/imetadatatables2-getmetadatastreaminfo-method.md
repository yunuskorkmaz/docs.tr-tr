---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables2:: Getmetadatastreaınfo yöntemi'
title: IMetaDataTables2::GetMetaDataStreamInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 323c31931cc97f18ff09df83c57153a3629d0a10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799255"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a>IMetaDataTables2::GetMetaDataStreamInfo Metodu

Belirtilen dizindeki meta veri akışının adını, boyutunu ve içeriğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ix`  
 'ndaki İstenen meta veri akışının dizini.  
  
 `ppchName`  
 dışı Akışın adına yönelik bir işaretçi.  
  
 `ppv`  
 dışı Meta veri akışına yönelik bir işaretçi.  
  
 `pcb`  
 dışı Bayt cinsinden boyutu `ppv` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
