---
description: 'Daha fazla bilgi edinin: CreateCoreClrDebugTarget Işlevi'
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
ms.openlocfilehash: 30a6af29e6e1a6ee2c827049a3c792f2d663a702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661583"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="7703d-103">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="7703d-103">CreateCoreClrDebugTarget Function</span></span>

<span data-ttu-id="7703d-104">Uzak makinede çalışan bir hata ayıklayıcı Proxy 'sine bir bağlantı oluşturur ve çalışan işlemlerin ve uzak makinedeki yüklü [](icoreclrdebugtarget-interface.md) çalışma zamanlarının sorgulanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7703d-104">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7703d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7703d-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7703d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7703d-106">Parameters</span></span>  

 `dwAddress`  
 <span data-ttu-id="7703d-107">'ndaki Uzak hedef makinenin IPv4 adresi.</span><span class="sxs-lookup"><span data-stu-id="7703d-107">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="7703d-108">dışı Oluşturulacak [ıreclrdebugtarget](icoreclrdebugtarget-interface.md) nesnesine yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7703d-108">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7703d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7703d-109">Return Value</span></span>  

 <span data-ttu-id="7703d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7703d-110">S_OK</span></span>  
 <span data-ttu-id="7703d-111">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="7703d-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="7703d-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7703d-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7703d-113">İçin yeterli bellek ayrılamıyor `ppTarget` .</span><span class="sxs-lookup"><span data-stu-id="7703d-113">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="7703d-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="7703d-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7703d-115">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="7703d-115">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7703d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7703d-116">Requirements</span></span>  

 <span data-ttu-id="7703d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7703d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7703d-118">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="7703d-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7703d-119">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7703d-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7703d-120">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7703d-120">**.NET Framework Versions:** 3.5 SP1</span></span>
