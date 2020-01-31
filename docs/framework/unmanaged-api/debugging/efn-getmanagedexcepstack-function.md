---
title: _EFN_GetManagedExcepStack İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789147"
---
# <a name="_efn_getmanagedexcepstack-function"></a>\_EFN\_GetManagedExcepStack Işlevi
Yönetilen bir özel durum nesne adresi verildiğinde, içinde bulunan yığın izlemenin bir dize sürümünü döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `Client`  
 'ndaki Hata ayıklamakta olan istemci.  
  
 `StackObjAddr`  
 'ndaki <xref:System.Exception>türetilen bir yönetilen nesne işaretçisi.  
  
 szStackString  
 dışı Döndürülen dize.  
  
 `cbString`  
 dışı Dize arabelleğinde kullanılabilir olan karakter sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda bağlamda iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace. h  
  
 **.NET Framework sürümü:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)
