---
description: ': ICLRMetaHost:: ExitProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3bc832538a5ad2b457de758fc35a632b09c02974
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689163"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="6df00-103">ICLRMetaHost::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6df00-103">ICLRMetaHost::ExitProcess Method</span></span>

<span data-ttu-id="6df00-104">Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="6df00-104">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="6df00-105">[CorExitProcess](corexitprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="6df00-105">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df00-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6df00-106">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6df00-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6df00-107">Parameters</span></span>  

 `iExitCode`  
 <span data-ttu-id="6df00-108">'ndaki İşlemin çıkış kodu.</span><span class="sxs-lookup"><span data-stu-id="6df00-108">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6df00-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6df00-109">Return Value</span></span>  

 <span data-ttu-id="6df00-110">Bu yöntem hiçbir şekilde döndürmez, bu nedenle dönüş değeri tanımsız olur.</span><span class="sxs-lookup"><span data-stu-id="6df00-110">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df00-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6df00-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df00-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6df00-112">Requirements</span></span>  

 <span data-ttu-id="6df00-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df00-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df00-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6df00-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6df00-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6df00-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6df00-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df00-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df00-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6df00-117">See also</span></span>

- [<span data-ttu-id="6df00-118">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df00-118">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="6df00-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="6df00-119">Hosting</span></span>](index.md)
