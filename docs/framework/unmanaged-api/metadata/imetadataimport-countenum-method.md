---
title: IMetaDataImport::CountEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: 4521a3f15ec358a4d786a4533efb6b99d0e1c1cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492388"
---
# <a name="imetadataimportcountenum-method"></a>IMetaDataImport::CountEnum Yöntemi
Belirtilen Numaralandırıcı tarafından alınan Numaralandırmadaki öğe sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hEnum`  
 'ndaki Numaralandırıcı için tanıtıcı.  
  
 `pulCount`  
 dışı Numaralandırılan öğe sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından belirtilen tanıtıcı, `hEnum` önceki bir `Enum` *ad* çağrısından alınır (örneğin, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
