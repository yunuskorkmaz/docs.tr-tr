---
description: 'Hakkında daha fazla bilgi edinin: LPOVERLAPPED_COMPLETION_ROUTINE Işlev Işaretçisi'
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
ms.openlocfilehash: 6645e6a9746404a4ae355a22cf16e6d164c63bed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679842"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi

Bir cihaza çakışan (yani zaman uyumsuz) g/ç tamamlandığında konağa bildiren bir işleve işaret eder.  
  
 Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwErrorCode`  
 'ndaki Cihaz kapatılmışsa hata kodu olan bir değer; Aksi takdirde, bu değer sıfırdır.  
  
 Bir cihazın kapatılması, cihazdaki tüm bekleyen g/ç 'nin hemen tamamlanmasını sağlar.  
  
 `dwNumberOfBytesTransfered`  
 'ndaki G/ç işlemi tarafından aktarılan bayt sayısı.  
  
 `lpOverlapped`  
 'ndaki G/ç isteğini tamambir şekilde gerçekleştirmek için kullanılacak bilgileri içeren bir yapıya yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `LPOVERLAPPED_COMPLETION_ROUTINE`Noktaların bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev. Geri arama işlevi, konağın tamamlanan g/ç isteğini işlemesini sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorWks.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
