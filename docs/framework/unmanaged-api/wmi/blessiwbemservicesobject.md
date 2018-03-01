---
title: "BlessIWbemServicesObject işlevi (yönetilmeyen API Başvurusu)"
description: "BlessIWbemServicesObject işlevi kullanıcı kimlik bilgilerini IWbemServices nesneyi erişime olup olmadığını gösterir"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2430358e5ea21468c2e975c2a26f20fe801ee546
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject işlevi
Kullanıcı kimlik bilgilerinin belirtilen erişime olup olmadığını gösteren [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) nesnesi.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parametreler

`pIWbemServices`  
[in] WMI hizmeti nesnesi için bir işaretçi.

`strUser`  
[in] Kullanıcı adı.

`strPassword`  
[in] İlişkili parolayı `strUser`.

`strAuthority`[in] Kullanıcının etki alanı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.

`impLevel`[in] Kimliğe bürünme düzeyi.

`authnLevel`[in] Kimlik doğrulama düzeyi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *Winerror.h'de* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Bir veya daha fazla bağımsız değişken geçersiz. |
| `E_POINTER` | 0x80004003 | `pIWbemServices`olan `null`. | 
| `E_FAIL` | 0x80000008 | Belirlenemeyen bir hata oluştu. |
| `E_OUTOFMEMORY` | 0x80000002 | İşlemi gerçekleştirmek yeterli bellek yok. | 
| `S_OK` | 0 | İşlev çağrısı başarısız oldu. | 

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
