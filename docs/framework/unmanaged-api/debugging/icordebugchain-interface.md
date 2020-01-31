---
title: ICorDebugChain Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: f4bacfe94178ea78b1c3afd15a2e100076c38a84
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777991"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain Arabirimi

Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateFrames Yöntemi](icordebugchain-enumerateframes-method.md)|En son kareyle başlayarak zincirdeki tüm yönetilen yığın çerçevelerini içeren bir Numaralandırıcı alır.|  
|[GetActiveFrame Yöntemi](icordebugchain-getactiveframe-method.md)|Zincirdeki etkin (yani en son) çerçeveyi alır.|  
|[GetCallee Yöntemi](icordebugchain-getcallee-method.md)|Bu zincir tarafından çağrılan zinciri alır.|  
|[GetCaller Yöntemi](icordebugchain-getcaller-method.md)|Bu zinciri çağıran zinciri alır.|  
|[GetContext Yöntemi](icordebugchain-getcontext-method.md)|Uygulanmadı.|  
|[GetNext Yöntemi](icordebugchain-getnext-method.md)|İş parçacığı için bir sonraki çerçeve zincirini alır.|  
|[GetPrevious Yöntemi](icordebugchain-getprevious-method.md)|İş parçacığı için önceki çerçeve zincirini alır.|  
|[GetReason Yöntemi](icordebugchain-getreason-method.md)|Bu çağrı zincirinin Genesin nedenini alır.|  
|[GetRegisterSet Yöntemi](icordebugchain-getregisterset-method.md)|Bu zincirin etkin bölümü için kayıt kümesini alır.|  
|[GetStackRange Yöntemi](icordebugchain-getstackrange-method.md)|Bu zincir için yığın segmentinin adres aralığını alır.|  
|[GetThread Yöntemi](icordebugchain-getthread-method.md)|Bu çağrı zincirinin parçası olduğu fiziksel iş parçacığını alır.|  
|[IsManaged Yöntemi](icordebugchain-ismanaged-method.md)|Bu zincirin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir zincirdeki yığın çerçeveleri bitişik yığın alanı kaplar ve aynı iş parçacığını ve bağlamı paylaşır. Bir zincir, yönetilen ya da yönetilmeyen kod zincirlerini temsil edebilir. Boş bir `ICorDebugChain` örneği, yönetilmeyen bir kod zincirini temsil eder.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
