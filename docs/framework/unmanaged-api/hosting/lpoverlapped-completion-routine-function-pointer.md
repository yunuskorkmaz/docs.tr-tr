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
ms.openlocfilehash: c0bdd9e59f5794dbb0d447dc2cc6cb682bfdf09f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008488"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="a53fd-102">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="a53fd-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="a53fd-103">Bir cihaza çakışan (yani zaman uyumsuz) g/ç tamamlandığında konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a53fd-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="a53fd-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a53fd-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a53fd-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a53fd-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a53fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a53fd-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="a53fd-107">'ndaki Cihaz kapatılmışsa hata kodu olan bir değer; Aksi takdirde, bu değer sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="a53fd-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="a53fd-108">Bir cihazın kapatılması, cihazdaki tüm bekleyen g/ç 'nin hemen tamamlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a53fd-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="a53fd-109">'ndaki G/ç işlemi tarafından aktarılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a53fd-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="a53fd-110">'ndaki G/ç isteğini tamambir şekilde gerçekleştirmek için kullanılacak bilgileri içeren bir yapıya yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a53fd-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a53fd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a53fd-111">Remarks</span></span>  
 <span data-ttu-id="a53fd-112">`LPOVERLAPPED_COMPLETION_ROUTINE`Noktaların bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev.</span><span class="sxs-lookup"><span data-stu-id="a53fd-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="a53fd-113">Geri arama işlevi, konağın tamamlanan g/ç isteğini işlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a53fd-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a53fd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a53fd-114">Requirements</span></span>  
 <span data-ttu-id="a53fd-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a53fd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a53fd-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a53fd-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a53fd-117">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="a53fd-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="a53fd-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a53fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a53fd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a53fd-119">See also</span></span>

- [<span data-ttu-id="a53fd-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a53fd-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
