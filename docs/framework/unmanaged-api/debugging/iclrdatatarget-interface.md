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
ms.openlocfilehash: 2b5c99e40aabdbc654bdc612729b2756e3ef5bb4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793710"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget Arabirimi
Ortak dil çalışma zamanının (CLR) hedef öğesiyle etkileşim için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCurrentThreadID Yöntemi](iclrdatatarget-getcurrentthreadid-method.md)|Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.|  
|[GetImageBase Yöntemi](iclrdatatarget-getimagebase-method.md)|Belirtilen görüntü için taban bellek adresini alır.|  
|[GetMachineType Yöntemi](iclrdatatarget-getmachinetype-method.md)|Hedef işlemin kullandığı yönerge kümesi türü için bir tanımlayıcı alır.|  
|[GetPointerSize Yöntemi](iclrdatatarget-getpointersize-method.md)|Geçerli hedefin bir işaretçisinin boyutunu bayt cinsinden alır.|  
|[GetThreadContext Yöntemi](iclrdatatarget-getthreadcontext-method.md)|Belirtilen tanımlayıcıya sahip iş parçacığı bağlamına yönelik bir işaretçi alır.|  
|[GetTLSValue Yöntemi](iclrdatatarget-gettlsvalue-method.md)|Belirtilen iş parçacığı için belirtilen dizindeki iş parçacığı yerel depolaması 'nda (TLS) bir değer alır.|  
|[ReadVirtual Yöntemi](iclrdatatarget-readvirtual-method.md)|Belirtilen sanal bellek adresinden belirtilen arabelleğe verileri okur.|  
|[Request Yöntemi](iclrdatatarget-request-method.md)|Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.|  
|[SetThreadContext Yöntemi](iclrdatatarget-setthreadcontext-method.md)|Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar.|  
|[SetTLSValue Yöntemi](iclrdatatarget-settlsvalue-method.md)|Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.|  
|[WriteVirtual Yöntemi](iclrdatatarget-writevirtual-method.md)|Belirtilen arabellekteki verileri belirtilen sanal bellek adresine yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
 API istemcisi (diğer bir deyişle, hata ayıklayıcı), bu arabirimin belirli bir hedef öğe için uygun şekilde uygulanması gerekir. Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget2 Arabirimi](iclrdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
