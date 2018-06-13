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
ms.openlocfilehash: a957eb6907b55fe948d696a6a25076c3950f7381
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402981"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="15e30-102">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="15e30-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="15e30-103">Uzak makinede çalışıyor ve döndüren bir hata ayıklayıcı proxy için bir bağlantı oluşturur bir [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) çalışan işlemleri ve uzak makinede yüklü çalışma zamanları sorgulamak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="15e30-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15e30-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15e30-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15e30-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="15e30-106">[in] Bir uzak hedef makinenin bir IPv4 adresi.</span><span class="sxs-lookup"><span data-stu-id="15e30-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="15e30-107">[out] Bir işaretçi işaretçi bir [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="15e30-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15e30-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="15e30-108">Return Value</span></span>  
 <span data-ttu-id="15e30-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="15e30-109">S_OK</span></span>  
 <span data-ttu-id="15e30-110">İşlem CLRs sayısında başarıyla belirlendi ve karşılık gelen tanıtıcısı ve yol dizileri düzgün doldurulmuş.</span><span class="sxs-lookup"><span data-stu-id="15e30-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="15e30-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="15e30-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="15e30-112">İçin yeterli bellek ayrılamıyor `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="15e30-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="15e30-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="15e30-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="15e30-114">Diğer hataları.</span><span class="sxs-lookup"><span data-stu-id="15e30-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e30-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15e30-115">Requirements</span></span>  
 <span data-ttu-id="15e30-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e30-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e30-117">**Başlık:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="15e30-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="15e30-118">**Kitaplığı:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="15e30-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="15e30-119">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="15e30-119">**.NET Framework Versions:** 3.5 SP1</span></span>
