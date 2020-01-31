---
title: ICorProfilerInfo9 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 371e85ce8f5d7b420a30ac842ec658949e47d30e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861651"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9 Arabirimi

Birden çok yerel kod sürümüne sahip işlevlerle ilgili bilgileri sorgulamak için yöntemler sağlayan bir [ICorProfilerInfo8](icorprofilerinfo8-interface.md) alt sınıfı.  

## <a name="methods"></a>Yöntemler  

| Yöntem|Açıklama|  
| ------------|-----------------|  
|[Getnativecodestartaadresler yöntemi](icorprofilerinfo9-getnativecodestartaddresses-method.md)| Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır. |
|[GetILToNativeMapping3 yöntemi](icorprofilerinfo9-getiltonativemapping3-method.md)| Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür. |
|[GetCodeInfo4 yöntemi](icorprofilerinfo9-getcodeinfo4-method.md)| Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür. |

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
