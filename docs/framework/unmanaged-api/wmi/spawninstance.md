---
title: SpawnInstance işlevi (yönetilmeyen API Başvurusu)
description: SpawnInstance işlev bir sınıfın yeni bir örneğini oluşturur.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74eb098ee68f57477c8b9115db2bce60919f0b12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580219"
---
# <a name="spawninstance-function"></a>SpawnInstance işlevi
Bir sınıfın yeni bir örneğini oluşturur.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`ppNewInstance`  
[out] Sınıfının yeni örneğini işaretçisi alır. Bir hata oluşursa, yeni bir nesne değil döndürdü ve `ppNewInstance` sol değiştirilmemiş.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` Geçerli bir sınıf tanımı değil ve yeni örnekleri oluşturma olamaz. Windows yönetimiyle çağırarak kayıtlı değil veya eksik olduğu [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` olan `null`. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemclassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) yöntemi.

`ptr` bir sınıf tanımı Windows yönetiminden alınmalıdır. (Bir örneği bir örnekten UNICODE desteklenir, ancak döndürülen örneği boş unutmayın.) Yeni örnekleri oluşturmak için bu sınıf tanımı kullanın. Bir çağrı [PutInstanceWmi](putinstancewmi.md) işlevi, örneği için Windows Yönetim yazmak istiyorsanız gereklidir.




Yeni Nesne döndürdü `ppNewClass` otomatik olarak geçerli nesne öğesinin alt sınıfı haline gelir. Bu davranışı geçersiz kılınamaz. Alt sınıflar (türetilmiş sınıflar) oluşturulabilmesi için diğer bir yöntem yoktur.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
