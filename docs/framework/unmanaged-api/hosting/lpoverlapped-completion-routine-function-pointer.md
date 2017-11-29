---
title: "LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPOVERLAPPED_COMPLETION_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords: LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d50f2058796d4c5c900474cdcbe71d8a5a911ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi
İşaret eden bir çakışan olduğunda ana bilgisayar bildiren bir işlev (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.  
  
 Bu işlev işaretçisi kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
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
 [in] Bir hata kodu cihaz kapattıysanız olan bir değer; Aksi takdirde, bu değer sıfır olur.  
  
 Bir aygıt kapatma neden olur. bekleyen g/ç aygıtı için hemen tamamlandı.  
  
 `dwNumberOfBytesTransfered`  
 [in] G/ç işlemi tarafından aktarılan bayt sayısı.  
  
 `lpOverlapped`  
 [in] G/ç isteği tamamlamak için kullanılacak bilgileri içeren bir yapı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşleve `LPOVERLAPPED_COMPLETION_ROUTINE` noktaları bir geri çağırma işlevidir ve barındırma uygulama yazıcı tarafından uygulanmalıdır. Tamamlanan g/ç isteği işlemek için ana geri çağırma işlevi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorWks.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
