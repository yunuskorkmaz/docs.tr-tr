---
title: CreateCordbObject İşlevi
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179229"
---
# <a name="createcordbobject-function"></a>CreateCordbObject İşlevi
Yönetilen hata ayıklama oturumunu uzak bir işlemde anında algılamak için işlevsellik sağlayan bir hata ayıklama arabirimi[(ICorDebug)](icordebug-interface.md)oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iDebuggerVersion`  
 [içinde] Hedef işlemin hata ayıklayıcı sürümü. Bu parametre uzaktan hata ayıklama için CorDebugVersion_2_0 olmalıdır.  
  
 `ppCordb`  
 [çıkış] [ICorDebug](icordebug-interface.md) arabirimine atılacak ve döndürülecek bir nesneye işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlemdeki CLR sayısı başarıyla belirlendi ve karşılık gelen tutamaç ve yol dizileri düzgün şekilde dolduruldu.  
  
 E_ınvalıdarg  
 `ppCordb`null veya `iDebuggerVersion` CorDebugVersion_2_0 değildir.  
  
 E_outofmemory  
 Için yeterli bellek ayrılamıyor`ppCordb`  
  
 E_FAIL (veya diğer E_ iade kodları)  
 Diğer başarısızlıklar.  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen [ICorDebug](icordebug-interface.md) `ppCordb` arabirimi, yönetilen tüm hata ayıklama hizmetleri için üst düzey hata ayıklama arabirimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Kütüphane:** mscordbi_macx86.dll  
  
 **.NET Çerçeve Sürümleri:** 3.5 SP1
