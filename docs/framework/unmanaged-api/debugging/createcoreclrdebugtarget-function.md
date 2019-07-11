---
title: CreateCoreClrDebugTarget İşlevi
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbcf6c842e7eee55609a9ea2a25cda4360f8dc95
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739292"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="4da7e-102">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="4da7e-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="4da7e-103">Uzak bir makinede çalışıyor ve döndüren bir hata ayıklayıcı proxy için bir bağlantı oluşturur bir [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) çalışan işlemleri ve uzak makinede yüklü çalışma zamanları sorgulamak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="4da7e-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da7e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4da7e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4da7e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4da7e-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="4da7e-106">[in] Bir uzak hedef makine IPv4 adresi.</span><span class="sxs-lookup"><span data-stu-id="4da7e-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="4da7e-107">[out] Bir işaretçi işaretçisi bir [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="4da7e-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4da7e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4da7e-108">Return Value</span></span>  
 <span data-ttu-id="4da7e-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="4da7e-109">S_OK</span></span>  
 <span data-ttu-id="4da7e-110">İşlem CLRs sayısında başarıyla belirlendi ve karşılık gelen tanıtıcısı ve yol diziler düzgün doldurulmuş.</span><span class="sxs-lookup"><span data-stu-id="4da7e-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="4da7e-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4da7e-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="4da7e-112">Yeterli bellek ayrılamıyor `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="4da7e-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="4da7e-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="4da7e-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4da7e-114">Diğer hatalar.</span><span class="sxs-lookup"><span data-stu-id="4da7e-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4da7e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4da7e-115">Requirements</span></span>  
 <span data-ttu-id="4da7e-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4da7e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4da7e-117">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="4da7e-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="4da7e-118">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="4da7e-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="4da7e-119">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="4da7e-119">**.NET Framework Versions:** 3.5 SP1</span></span>
