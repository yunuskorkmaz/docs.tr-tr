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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789189"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="22005-102">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="22005-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="22005-103">Uzak makinede çalışan bir hata ayıklayıcı Proxy 'sine bir bağlantı oluşturur ve çalışan işlemlerin ve uzak makinedeki yüklü [](icoreclrdebugtarget-interface.md) çalışma zamanlarının sorgulanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="22005-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22005-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22005-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22005-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22005-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="22005-106">'ndaki Uzak hedef makinenin IPv4 adresi.</span><span class="sxs-lookup"><span data-stu-id="22005-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="22005-107">dışı Oluşturulacak [ıreclrdebugtarget](icoreclrdebugtarget-interface.md) nesnesine yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="22005-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22005-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="22005-108">Return Value</span></span>  
 <span data-ttu-id="22005-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="22005-109">S_OK</span></span>  
 <span data-ttu-id="22005-110">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="22005-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="22005-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="22005-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="22005-112">`ppTarget`için yeterli bellek ayrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="22005-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="22005-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="22005-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="22005-114">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="22005-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22005-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22005-115">Requirements</span></span>  
 <span data-ttu-id="22005-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22005-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22005-117">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="22005-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="22005-118">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="22005-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="22005-119">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="22005-119">**.NET Framework Versions:** 3.5 SP1</span></span>
