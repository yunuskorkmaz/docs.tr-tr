---
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
ms.openlocfilehash: a5a86df3ac1f50ca624490ad80a6fed903433436
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762376"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="2aadf-102">ICorRuntimeHost::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2aadf-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="2aadf-103">Bir etki alanı numaralandırıcısını etki alanı listesinin başına geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2aadf-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aadf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2aadf-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2aadf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2aadf-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="2aadf-106">'ndaki Sıfırlanacak Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="2aadf-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2aadf-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2aadf-107">Return Value</span></span>  
  
|<span data-ttu-id="2aadf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2aadf-108">HRESULT</span></span>|<span data-ttu-id="2aadf-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2aadf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2aadf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2aadf-110">S_OK</span></span>|<span data-ttu-id="2aadf-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="2aadf-111">The operation was successful.</span></span>|  
|<span data-ttu-id="2aadf-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2aadf-112">S_FALSE</span></span>|<span data-ttu-id="2aadf-113">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="2aadf-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="2aadf-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2aadf-114">E_FAIL</span></span>|<span data-ttu-id="2aadf-115">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2aadf-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="2aadf-116">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2aadf-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="2aadf-117">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2aadf-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2aadf-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2aadf-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2aadf-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2aadf-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2aadf-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2aadf-120">Requirements</span></span>  
 <span data-ttu-id="2aadf-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aadf-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aadf-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2aadf-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2aadf-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2aadf-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2aadf-124">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="2aadf-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aadf-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2aadf-125">See also</span></span>

- [<span data-ttu-id="2aadf-126">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="2aadf-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="2aadf-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2aadf-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
