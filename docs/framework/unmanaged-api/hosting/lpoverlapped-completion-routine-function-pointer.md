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
ms.openlocfilehash: cd4b7ffef9c0ba3aba54387245b2d5c9ec1ae906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441762"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="459b2-102">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="459b2-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="459b2-103">İşaret eden bir çakışan olduğunda ana bilgisayar bildiren bir işlev (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="459b2-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="459b2-104">Bu işlev işaretçisi kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="459b2-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="459b2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="459b2-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="459b2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="459b2-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="459b2-107">[in] Bir hata kodu cihaz kapattıysanız olan bir değer; Aksi takdirde, bu değer sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="459b2-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="459b2-108">Bir aygıt kapatma neden olur. bekleyen g/ç aygıtı için hemen tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="459b2-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="459b2-109">[in] G/ç işlemi tarafından aktarılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="459b2-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="459b2-110">[in] G/ç isteği tamamlamak için kullanılacak bilgileri içeren bir yapı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="459b2-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="459b2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="459b2-111">Remarks</span></span>  
 <span data-ttu-id="459b2-112">İşleve `LPOVERLAPPED_COMPLETION_ROUTINE` noktaları bir geri çağırma işlevidir ve barındırma uygulama yazıcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="459b2-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="459b2-113">Tamamlanan g/ç isteği işlemek için ana geri çağırma işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="459b2-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="459b2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="459b2-114">Requirements</span></span>  
 <span data-ttu-id="459b2-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="459b2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="459b2-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="459b2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="459b2-117">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="459b2-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="459b2-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="459b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459b2-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="459b2-119">See Also</span></span>  
 [<span data-ttu-id="459b2-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="459b2-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
