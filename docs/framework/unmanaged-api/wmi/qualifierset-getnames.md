---
title: QualifierSet_GetNames işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_GetNames işlevi, bir nesneye veya özelliğe niteleyicileri adlarını alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84059c5e5542e13b1d4fc4efcfc4c7f418db391e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276922"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames işlevi
Tüm niteleyicileri veya geçerli nesne ya da özellik mevcut olan bazı niteleyicileri adlarını alır. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
[in] Bu parametre kullanılmaz.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.

`lFlags`   
[in] Aşağıdaki bayrakları veya numaralandırmada dahil etmek için hangi adlarını belirten değerlerinden biri.

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|  | 0 | Tüm niteleyicileri adlarını döndürür. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca niteleyicileri adları belirli için geçerli bir özellik veya nesne döndürür. <br/> Bir özellik için: yalnızca niteleyicileri (geçersiz kılmaları dahil) özelliğine belirli dönün ve bu niteleyicileri, sınıf tanımından yayılır. <br/> Bir örneği için: yalnızca örnek özgü niteleyicisi adlarını döndürür. <br/> Bir sınıf için: türetilmiş sınıf beiong yalnızca niteleyicileri belirli döndürür.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Başka bir nesnenin dönüş yalnızca niteleyicileri adlarını yayılır. <br/> Bir özellik için: Bu özellik sınıf tanımı ve özelliğinden olanlar yalnızca niteleyicileri yayılan dönün. <br/> Bir örneği için: sınıf tanımının dönüş niteleyicileri yalnızca yayılır. <br/> Bir sınıf için: Bu niteleyici adları yalnızca üst sınıflardan devralınır Return. |

`pstrNames` [out] Yeni bir `SAFEARRAY` , istenen adlarını içerir. Dizi öğeleri 0 olabilir. Bir hata oluşursa, yeni bir `SAFEARRAY` döndürülmez.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) yöntemi.

Siz niteleyicisi adları aldıktan sonra her niteleyicisi adına göre çağırarak erişebilirsiniz [QualifierSet_Get](qualifierset-get.md) işlevi. 

Sıfır niteleyicileri olması belirli bir nesne için bir hata değil dizelerde sayısını `pstrNames` işlevi döndürür olsa bile getirisini 0 olabilir `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
