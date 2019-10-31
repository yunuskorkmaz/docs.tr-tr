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
ms.openlocfilehash: d52757f82a950c382c7c8f2162630eda7d7795e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132102"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="2c352-102">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="2c352-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="2c352-103">Uzak makinede çalışan bir hata ayıklayıcı Proxy 'sine bir bağlantı oluşturur ve çalışan işlemlerin ve uzak makinedeki yüklü [](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) çalışma zamanlarının sorgulanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2c352-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c352-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c352-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c352-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c352-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="2c352-106">'ndaki Uzak hedef makinenin IPv4 adresi.</span><span class="sxs-lookup"><span data-stu-id="2c352-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="2c352-107">dışı Oluşturulacak [ıreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) nesnesine yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2c352-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c352-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2c352-108">Return Value</span></span>  
 <span data-ttu-id="2c352-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c352-109">S_OK</span></span>  
 <span data-ttu-id="2c352-110">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="2c352-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="2c352-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2c352-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="2c352-112">`ppTarget`için yeterli bellek ayrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2c352-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="2c352-113">E_FAıL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="2c352-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="2c352-114">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="2c352-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c352-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c352-115">Requirements</span></span>  
 <span data-ttu-id="2c352-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c352-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c352-117">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="2c352-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="2c352-118">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="2c352-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="2c352-119">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="2c352-119">**.NET Framework Versions:** 3.5 SP1</span></span>
