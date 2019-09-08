---
title: Blessıwbemservices işlevi (yönetilmeyen API Başvurusu)
description: Blessıwbemservices işlevi, Kullanıcı kimlik bilgilerinin bir IWbemServices sınıfına erişime izin verip vermediğini belirtir.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ab5eb418b5f0a9175074c87837c7cac8936346
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799052"
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices işlevi
Kullanıcı kimlik bilgilerinin belirtilen [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) sınıfına erişime izin verip vermediğini belirtir.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parametreler

`pIWbemServices`\
'ndaki İzinleri gerekli olan [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine yönelik bir işaretçi.

`strUser`\
'ndaki Kullanıcı adı.

`strPassword`\
'ndaki İle `strUser`ilişkili parola.

`strAuthority`\
'ndaki Kullanıcının etki alanı adı. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

`impLevel`\
'ndaki Kimliğe bürünme düzeyi.

`authnLevel`\
'ndaki Yetkilendirme düzeyi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler *Winerror. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Bir veya daha fazla bağımsız değişken geçersiz. |
| `E_POINTER` | 0x80004003 | `pIWbemServices``null`. | 
| `E_FAIL` | 0x80000008 | Belirtilmeyen bir hata oluştu. |
| `E_OUTOFMEMORY` | 0x80000002 | İşlemi gerçekleştirmek için yeterli bellek yok. | 
| `S_OK` | 0 | İşlev çağrısı başarılı oldu. | 

## <a name="requirements"></a>Gereksinimler  

 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
