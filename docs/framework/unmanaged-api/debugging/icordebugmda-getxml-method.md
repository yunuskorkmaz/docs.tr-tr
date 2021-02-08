---
description: ': ICorDebugMDA:: GetXML yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugMDA::GetXML Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: fa506e6e8f306271f10a7a715af9b8bc6a80c1d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801143"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML Yöntemi

[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ILIŞKILI tam XML akışını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cchName`  
 'ndaki `szName` Dizinin boyutu.  
  
 `pcchName`  
 dışı XML akışının uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı XML akışının depolandığı bir dizi. Dizi boş olabilir.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetXML`Yöntemi, ILIŞKILI XML akışının boyutuna bağlı olarak performansı etkileyebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMDA Arabirimi](icordebugmda-interface.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
