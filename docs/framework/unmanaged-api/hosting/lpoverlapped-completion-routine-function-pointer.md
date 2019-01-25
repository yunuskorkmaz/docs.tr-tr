---
title: LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2c3040adddabee716976d778c29d1f6729efc39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576934"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi
Tamamlandığı zaman ana bilgisayara bildiren bir işleve işaret eder (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.  
  
 Bu işlev işaretçisi içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwErrorCode`  
 [in] Cihaz kapattıysanız, bir hata kodu değeri; Aksi takdirde, bu değeri sıfırdır.  
  
 Bir cihazı kapatma neden bekleyen g/ç cihaza hemen tamamlanacak.  
  
 `dwNumberOfBytesTransfered`  
 [in] G/ç işlemi tarafından aktarılan bayt sayısı.  
  
 `lpOverlapped`  
 [in] I/O isteğini tamamlamak için kullanılacak bilgileri içeren bir yapıya bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşleve `LPOVERLAPPED_COMPLETION_ROUTINE` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır. Tamamlanan g/ç isteği işlemek için ana geri çağırma işlevi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorWks.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
