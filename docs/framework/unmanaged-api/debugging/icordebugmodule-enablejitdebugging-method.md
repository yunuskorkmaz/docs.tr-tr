---
description: ': ICorDebugModule:: Enablejıdebugging yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugModule::EnableJITDebugging Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: 30077bd586e1cb9cb8766290804e31f5999d9e72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722691"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging Yöntemi

Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bTrackJITInfo`  
 'ndaki Bu `true` modüldeki, Microsoft ara dili (MSIL) sürümü ve bu modüldeki her YÖNTEMIN JIT derlenmiş sürümü arasındaki eşleme bilgilerini korumak için bu değeri olarak ayarlayın.  
  
 `bAllowJitOpts`  
 'ndaki `true` JIT derleyicisinin hata ayıklama için belirli BIR JIT özel iyileştirmelere sahip kod oluşturmasını sağlamak için bu değeri olarak ayarlayın.  
  
## <a name="remarks"></a>Açıklamalar  

 JıT hata ayıklayıcı, hata ayıklayıcısı etkin olduğunda yüklenen tüm modüller için varsayılan olarak etkindir. Ayarları programlı bir şekilde etkinleştirmek veya devre dışı bırakmak genel ayarları geçersiz kılar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
