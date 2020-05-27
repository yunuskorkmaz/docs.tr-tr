---
title: ICeeGen::GetSectionDataLen Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 1855c73849c35bf709b0af261a88e6cd7a40abfb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008306"
---
# <a name="iceegengetsectiondatalen-method"></a>ICeeGen::GetSectionDataLen Yöntemi
Belirtilen bölümün uzunluğunu alır.  
  
 Bu yöntem kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `section`  
 'ndaki Uzunluğu alınacak olan veri bölümü.  
  
 `dataLen`  
 dışı Belirtilen bölümün döndürdüğü uzunluğu.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSectionDataLen`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICeeGen Arabirimi](iceegen-interface.md)
