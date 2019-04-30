---
title: ICLRDataTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed3cb62b56e80a7fe4ea54b43ac9f4a28b8d102
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698115"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget Arabirimi
Bir hedef öğesi ortak dil çalışma zamanı (CLR) etkileşim için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCurrentThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.|  
|[GetImageBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Belirtilen görüntü için temel bir bellek adresi alır.|  
|[GetMachineType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Hedef işlemin kullandığı yönerge kümesi türü için bir tanımlayıcı alır.|  
|[GetPointerSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Boyutu bayt cinsinden geçerli bir hedef için bir işaretçi alır.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Bir işaretçi belirtilen tanımlayıcı ile iş parçacığı için bağlamı alır.|  
|[GetTLSValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Belirtilen dizindeki belirtilen iş parçacığı için iş parçacığı yerel depolaması (TLS) bir değer alır.|  
|[ReadVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Veri belirtilen sanal bellek adresinden belirtilen arabelleğe okur.|  
|[Request Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Uygulama tarafından tanımlanan bir işlemi istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.|  
|[SetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Belirtilen iş parçacığının geçerli bağlam hedef işlemde ayarlar.|  
|[SetTLSValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama (TLS) bir değer ayarlar.|  
|[WriteVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Verileri belirtilen arabellek belirtilen sanal bellek adresini yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
 API istemcisi (diğer bir deyişle, hata ayıklayıcı) bu arabirimi belirli hedef öğe için uygun şekilde uygulamalıdır. Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
