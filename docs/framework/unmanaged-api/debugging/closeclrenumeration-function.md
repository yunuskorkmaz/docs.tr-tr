---
title: CloseCLREnumeration İşlevi
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a05a779d4a56eb8f881da1824d5ffaa363b5a01
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274276"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration İşlevi
Geçerli ortak dil çalışma zamanı (CLR) Continue-, [EnumerateCLRs işlevi](enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan Başlangıç olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pHandleArray`  
 'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen olay tanıtıcısı dizisine yönelik işaretçi.  
  
 `pStringArray`  
 'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen CLR dize yollarının dizisine yönelik işaretçi.  
  
 `dwArrayLength`  
 'ndaki `pHandleArray` Ya`pStringArray` da (uzunluk) boyutunu (aynı) içeren DWORD.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 [EnumerateCLRs işlevi](enumerateclrs-function.md) tarafından açılan tutamaçlar kapatılır ve tanıtıcı ve dize dizileri için ayrılan bellek serbest bırakılır.  
  
 E_INVALIDARG  
 `pHandleArray` Uzunluğu`dwArrayLength`geçilen uzunlukla eşleşmiyor.  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 İşlevi ve `pHandleArray` `pStringArray`için belleği serbest bırakılamıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3.5 SP1
