---
title: ICLRMetaHost::ExitProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 83cbfa097541681305ff285f21c2b6c9c6391ef8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703752"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="d9d8a-102">ICLRMetaHost::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9d8a-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="d9d8a-103">Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="d9d8a-104">[CorExitProcess](corexitprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-104">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d8a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d9d8a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9d8a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9d8a-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="d9d8a-107">'ndaki İşlemin çıkış kodu.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9d8a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9d8a-108">Return Value</span></span>  
 <span data-ttu-id="d9d8a-109">Bu yöntem hiçbir şekilde döndürmez, bu nedenle dönüş değeri tanımsız olur.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9d8a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9d8a-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d8a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9d8a-111">Requirements</span></span>  
 <span data-ttu-id="d9d8a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9d8a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d8a-113">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d9d8a-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d9d8a-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d9d8a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9d8a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d8a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d8a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9d8a-116">See also</span></span>

- [<span data-ttu-id="d9d8a-117">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9d8a-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="d9d8a-118">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d9d8a-118">Hosting</span></span>](index.md)
