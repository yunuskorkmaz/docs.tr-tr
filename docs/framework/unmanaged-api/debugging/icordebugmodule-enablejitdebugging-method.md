---
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
ms.openlocfilehash: bdf027f94c8416d052cb807d04be76a39868ccf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212938"
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
 'ndaki `true`JIT derleyicisinin hata ayıklama için belirli BIR JIT özel iyileştirmelere sahip kod oluşturmasını sağlamak için bu değeri olarak ayarlayın.  
  
## <a name="remarks"></a>Açıklamalar  
 JıT hata ayıklayıcı, hata ayıklayıcısı etkin olduğunda yüklenen tüm modüller için varsayılan olarak etkindir. Ayarları programlı bir şekilde etkinleştirmek veya devre dışı bırakmak genel ayarları geçersiz kılar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
