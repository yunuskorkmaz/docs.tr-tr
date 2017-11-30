---
title: ICLRDataTarget Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a40276b28f3d20428f0d7eb0556a762fdb56801
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget Arabirimi
Ortak dil çalışma zamanı (CLR) hedef öğesinin etkileşim için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Getcurrentthreadıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.|  
|[Getımagebase yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Temel bellek adresi için belirtilen görüntü alır.|  
|[GetMachineType yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Hedef işlemin kullanarak yönerge kümesi türü için bir tanımlayıcı alır.|  
|[GetPointerSize yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Bayt olarak geçerli hedefi bir işaretçi boyutunu alır.|  
|[GetThreadContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Bir işaretçi belirtilen tanımlayıcı ile iş parçacığı bağlamına alır.|  
|[GetTLSValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Belirtilen dizine belirtilen iş parçacığı için iş parçacığı yerel depolaması (TLS) bir değer alır.|  
|[ReadVirtual yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Verileri belirtilen sanal bellek adresinden belirtilen arabelleğe okur.|  
|[İstek yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Uygulama tarafından tanımlandığı şekilde, bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.|  
|[SetThreadContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Belirtilen iş parçacığı geçerli bağlamı hedef işleminde ayarlar.|  
|[SetTLSValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Belirtilen iş parçacığının hedef işlemdeki iş parçacığı yerel depolaması (TLS) içinde bir değer ayarlar.|  
|[WriteVirtual yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Verileri belirtilen arabelleğinden belirtilen sanal bellek adresi yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
 API istemcisi (hata ayıklayıcı) belirli hedef öğesi için uygun şekilde bu arabirimi uygulamalıdır. Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrdatatarget2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
