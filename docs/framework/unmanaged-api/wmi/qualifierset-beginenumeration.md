---
title: QualifierSet_BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: Bir nesnenin niteleyicileri numaralandırması QualifierSet_BeginEnumeration işlevi sıfırlar.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d20701237501834c611c4e498c39597cf275176
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518692"
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration işlevi
Bir nesnenin niteleyicileri numaralandırması sabit başlangıcına sıfırlar.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
[in] Bu parametre kullanılmaz.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.

`lFlags`   
[in] Bayrakları veya açıklanan değerler Bitsel bir birleşimi [açıklamalar](#remarks) numaralandırmada içerecek şekilde niteleyicileri belirten bölüm.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametresi geçerli değil. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | İkinci çağrı `QualifierSet_BeginEnumeration` bir çağrı göndermelisiniz olmadan yapılan [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) yöntemi.

Tüm nesne üzerindeki niteleyiciler numaralandırmak için bu yöntem ilk çağırmadan önce çağrılmalıdır [QualifierSet_Next](qualifierset-next.md). Niteleyiciler numaralandırılan siparişi için belirli bir numaralandırma sabit olması sağlanır.

Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişken tanımlanmış *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda.   

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|  | 0 | Tüm niteleyicileri adlarını döndürür. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca niteleyicileri adları belirli için geçerli bir özellik veya nesne döndürür. <br/> Bir özellik için: yalnızca niteleyicileri (geçersiz kılmaları dahil) özelliğine belirli dönün ve bu niteleyicileri, sınıf tanımından yayılır. <br/> Bir örneği için: yalnızca örnek özgü niteleyicisi adlarını döndürür. <br/> Bir sınıf için: türetilmiş sınıf beiong yalnızca niteleyicileri belirli döndürür.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Başka bir nesnenin dönüş yalnızca niteleyicileri adlarını yayılır. <br/> Bir özellik için: Bu özellik sınıf tanımı ve özelliğinden olanlar yalnızca niteleyicileri yayılan dönün. <br/> Bir örneği için: sınıf tanımının dönüş niteleyicileri yalnızca yayılır. <br/> Bir sınıf için: Bu niteleyici adları yalnızca üst sınıflardan devralınır Return. |

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
