---
description: ': IHostMemoryManager:: VirtualProtect yöntemi hakkında daha fazla bilgi edinin'
title: IHostMemoryManager::VirtualProtect Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
ms.openlocfilehash: 66e1fb5afdc3aa5c400ed0ffa9cea569d300e6a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707455"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="b81a4-103">IHostMemoryManager::VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b81a4-103">IHostMemoryManager::VirtualProtect Method</span></span>

<span data-ttu-id="b81a4-104">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="b81a4-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="b81a4-105">' Nin Win32 uygulamasında, `VirtualProtect` çağıran işlemin sanal adres alanındaki bir kaydedilmiş sayfalar bölgesinde koruma değişir.</span><span class="sxs-lookup"><span data-stu-id="b81a4-105">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b81a4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b81a4-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b81a4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b81a4-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="b81a4-108">'ndaki Koruma öznitelikleri değiştirilecek olan sanal belleğin temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b81a4-108">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="b81a4-109">'ndaki Değiştirilecek bellek sayfaları bölgesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b81a4-109">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="b81a4-110">'ndaki Uygulanacak bellek koruması türü.</span><span class="sxs-lookup"><span data-stu-id="b81a4-110">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="b81a4-111">dışı Önceki bellek koruma değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b81a4-111">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b81a4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b81a4-112">Return Value</span></span>  
  
|<span data-ttu-id="b81a4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b81a4-113">HRESULT</span></span>|<span data-ttu-id="b81a4-114">Description</span><span class="sxs-lookup"><span data-stu-id="b81a4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b81a4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b81a4-115">S_OK</span></span>|<span data-ttu-id="b81a4-116">`VirtualProtect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b81a4-116">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="b81a4-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b81a4-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b81a4-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b81a4-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b81a4-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b81a4-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b81a4-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b81a4-120">The call timed out.</span></span>|  
|<span data-ttu-id="b81a4-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b81a4-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b81a4-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b81a4-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b81a4-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b81a4-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b81a4-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b81a4-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b81a4-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b81a4-125">E_FAIL</span></span>|<span data-ttu-id="b81a4-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b81a4-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b81a4-127">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b81a4-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b81a4-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b81a4-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b81a4-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b81a4-129">Remarks</span></span>  

 <span data-ttu-id="b81a4-130">Bu uygulama, `VirtualProtect` BIR HRESULT değeri döndürür, ancak Win32 uygulamasının başarılı olduğunu belirtmek için sıfır olmayan bir değer ve hatayı göstermek için sıfır değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b81a4-130">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="b81a4-131">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="b81a4-131">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b81a4-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b81a4-132">Requirements</span></span>  

 <span data-ttu-id="b81a4-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b81a4-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b81a4-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b81a4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b81a4-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b81a4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b81a4-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b81a4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81a4-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b81a4-137">See also</span></span>

- [<span data-ttu-id="b81a4-138">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b81a4-138">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
