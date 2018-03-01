---
title: "LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b1846cf8fff5c41fc54ddeec5b495b50c63581c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="1f444-102">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="1f444-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="1f444-103">İşaret eden bir çakışan olduğunda ana bilgisayar bildiren bir işlev (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1f444-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="1f444-104">Bu işlev işaretçisi kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f444-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f444-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f444-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f444-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f444-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="1f444-107">[in] Bir hata kodu cihaz kapattıysanız olan bir değer; Aksi takdirde, bu değer sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="1f444-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="1f444-108">Bir aygıt kapatma neden olur. bekleyen g/ç aygıtı için hemen tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1f444-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="1f444-109">[in] G/ç işlemi tarafından aktarılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f444-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="1f444-110">[in] G/ç isteği tamamlamak için kullanılacak bilgileri içeren bir yapı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f444-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f444-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f444-111">Remarks</span></span>  
 <span data-ttu-id="1f444-112">İşleve `LPOVERLAPPED_COMPLETION_ROUTINE` noktaları bir geri çağırma işlevidir ve barındırma uygulama yazıcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f444-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="1f444-113">Tamamlanan g/ç isteği işlemek için ana geri çağırma işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f444-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f444-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f444-114">Requirements</span></span>  
 <span data-ttu-id="1f444-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f444-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f444-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f444-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f444-117">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="1f444-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="1f444-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f444-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f444-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f444-119">See Also</span></span>  
 [<span data-ttu-id="1f444-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1f444-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
