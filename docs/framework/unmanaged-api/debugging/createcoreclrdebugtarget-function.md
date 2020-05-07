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
ms.openlocfilehash: 2271611b5cbbfe487e5798be0429ed94c227a67f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860874"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="d31ce-102">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="d31ce-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="d31ce-103">Uzak makinede çalışan bir hata ayıklayıcı Proxy 'sine bir bağlantı oluşturur ve çalışan işlemlerin ve uzak makinedeki yüklü [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) çalışma zamanlarının sorgulanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d31ce-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d31ce-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d31ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d31ce-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="d31ce-106">'ndaki Uzak hedef makinenin IPv4 adresi.</span><span class="sxs-lookup"><span data-stu-id="d31ce-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="d31ce-107">dışı Oluşturulacak [ıreclrdebugtarget](icoreclrdebugtarget-interface.md) nesnesine yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d31ce-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d31ce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d31ce-108">Return Value</span></span>  
 <span data-ttu-id="d31ce-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="d31ce-109">S_OK</span></span>  
 <span data-ttu-id="d31ce-110">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="d31ce-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="d31ce-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d31ce-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="d31ce-112">İçin `ppTarget`yeterli bellek ayrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="d31ce-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="d31ce-113">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="d31ce-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d31ce-114">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="d31ce-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d31ce-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d31ce-115">Requirements</span></span>  
 <span data-ttu-id="d31ce-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d31ce-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d31ce-117">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="d31ce-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d31ce-118">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="d31ce-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d31ce-119">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d31ce-119">**.NET Framework Versions:** 3.5 SP1</span></span>
