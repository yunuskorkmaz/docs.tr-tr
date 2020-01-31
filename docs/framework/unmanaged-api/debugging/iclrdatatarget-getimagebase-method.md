---
title: ICLRDataTarget::GetImageBase Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
ms.openlocfilehash: fcf0ab73c79a5fa116a89cdfcc2e73b17d9eabfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785487"
---
# <a name="iclrdatatargetgetimagebase-method"></a>ICLRDataTarget::GetImageBase Yöntemi
Belirtilen görüntünün taban bellek adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `imagePath`  
 'ndaki Görüntünün yolu da dahil olmak üzere dosya adı.  
  
 `baseAddress`  
 dışı Görüntünün temel adresini depolayan CLRDATA_ADDRESS işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Görüntü dosyası adı bir yola sahip olabilir veya olmayabilir. Bir yol belirtilmişse, eşleşme tam yol üzerinde yapılır; Aksi takdirde, eşleştirme yalnızca dosya adı üzerinde yapılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
