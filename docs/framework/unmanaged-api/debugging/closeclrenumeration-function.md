---
description: 'Daha fazla bilgi edinin: CloseCLREnumeration Işlevi'
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
ms.openlocfilehash: 7669332cc23b78afbb3bf597e7d208a5f707aae5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772776"
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
 'ndaki Ya da (uzunluk) boyutunu ( `pHandleArray` aynı) IÇEREN DWORD `pStringArray` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 S_OK  
 [EnumerateCLRs işlevi](enumerateclrs-function.md) tarafından açılan tutamaçlar kapatılır ve tanıtıcı ve dize dizileri için ayrılan bellek serbest bırakılır.  
  
 E_INVALIDARG  
 Uzunluğu `pHandleArray` geçilen uzunlukla eşleşmiyor `dwArrayLength` .  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 İşlevi ve için belleği serbest bırakılamıyor `pHandleArray` `pStringArray` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim.dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
