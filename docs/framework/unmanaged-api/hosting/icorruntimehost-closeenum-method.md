---
description: ': ICorRuntimeHost:: CloseEnum Yöntemi hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::CloseEnum Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: 1fc18ff3e00f85a4f047417f880ec2b0e06496b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789729"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="ceb47-103">ICorRuntimeHost::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceb47-103">ICorRuntimeHost::CloseEnum Method</span></span>

<span data-ttu-id="ceb47-104">Bir etki alanı numaralandırıcısını etki alanı listesinin başına geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ceb47-104">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb47-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ceb47-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceb47-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ceb47-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="ceb47-107">'ndaki Sıfırlanacak Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="ceb47-107">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ceb47-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ceb47-108">Return Value</span></span>  
  
|<span data-ttu-id="ceb47-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ceb47-109">HRESULT</span></span>|<span data-ttu-id="ceb47-110">Description</span><span class="sxs-lookup"><span data-stu-id="ceb47-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ceb47-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ceb47-111">S_OK</span></span>|<span data-ttu-id="ceb47-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ceb47-112">The operation was successful.</span></span>|  
|<span data-ttu-id="ceb47-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ceb47-113">S_FALSE</span></span>|<span data-ttu-id="ceb47-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="ceb47-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ceb47-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ceb47-115">E_FAIL</span></span>|<span data-ttu-id="ceb47-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ceb47-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ceb47-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ceb47-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ceb47-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ceb47-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ceb47-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ceb47-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ceb47-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ceb47-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ceb47-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ceb47-121">Requirements</span></span>  

 <span data-ttu-id="ceb47-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceb47-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb47-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ceb47-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ceb47-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ceb47-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ceb47-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="ceb47-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb47-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceb47-126">See also</span></span>

- [<span data-ttu-id="ceb47-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="ceb47-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="ceb47-128">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ceb47-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
