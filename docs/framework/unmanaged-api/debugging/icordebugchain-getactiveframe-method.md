---
title: ICorDebugChain::GetActiveFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: daecd216b4d7e9c23336b8956c13735549be901b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730142"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame Metodu

Zincirdeki etkin (yani en son) çerçeveyi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppFrame`  
 dışı Zincirdeki etkin (yani en son) kareyi temsil eden ICorDebugFrame nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Kullanılabilir bir yönetilen yığın çerçevesi yoksa, `ppFrame` null olarak ayarlanır.  
  
 Etkin çerçeve kullanılabilir değilse, çağrı başarılı olur ve `ppFrame` null olur. CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirler için etkin çerçeveler kullanılamaz ve bazı zincirler CHAIN_CLASS_INIT nedeniyle başlatılmış olur. CorDebugChainReason numaralandırması bölümüne bakın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
