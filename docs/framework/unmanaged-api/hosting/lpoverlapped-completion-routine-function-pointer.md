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
ms.openlocfilehash: dcf63000de549b42d92ba157a7e550ac605bbfcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768384"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="efd8d-102">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="efd8d-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="efd8d-103">Tamamlandığı zaman ana bilgisayara bildiren bir işleve işaret eder (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="efd8d-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="efd8d-104">Bu işlev işaretçisi .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="efd8d-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd8d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efd8d-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd8d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efd8d-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="efd8d-107">[in] Cihaz kapattıysanız, bir hata kodu değeri; Aksi takdirde, bu değeri sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="efd8d-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="efd8d-108">Bir cihazı kapatma neden bekleyen g/ç cihaza hemen tamamlanacak.</span><span class="sxs-lookup"><span data-stu-id="efd8d-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="efd8d-109">[in] G/ç işlemi tarafından aktarılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="efd8d-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="efd8d-110">[in] I/O isteğini tamamlamak için kullanılacak bilgileri içeren bir yapıya bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efd8d-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efd8d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efd8d-111">Remarks</span></span>  
 <span data-ttu-id="efd8d-112">İşleve `LPOVERLAPPED_COMPLETION_ROUTINE` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="efd8d-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="efd8d-113">Tamamlanan g/ç isteği işlemek için ana geri çağırma işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="efd8d-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd8d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efd8d-114">Requirements</span></span>  
 <span data-ttu-id="efd8d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd8d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd8d-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="efd8d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efd8d-117">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="efd8d-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="efd8d-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd8d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd8d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efd8d-119">See also</span></span>

- [<span data-ttu-id="efd8d-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="efd8d-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
