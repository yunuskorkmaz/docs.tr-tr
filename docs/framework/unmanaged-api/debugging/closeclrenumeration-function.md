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
ms.openlocfilehash: 1d42292705dae03e9bf1a1555508dfb69cebde82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132429"
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
 'ndaki `pHandleArray` ya da `pStringArray` boyutunu (uzunluk) içeren DWORD (aynı).  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 [EnumerateCLRs işlevi](enumerateclrs-function.md) tarafından açılan tutamaçlar kapatılır ve tanıtıcı ve dize dizileri için ayrılan bellek serbest bırakılır.  
  
 E_INVALIDARG  
 `pHandleArray` uzunluğu `dwArrayLength`geçirilen uzunluğa uymuyor.  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 İşlev, `pHandleArray` ve `pStringArray`için belleği serbest gönderemedi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
