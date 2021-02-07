---
description: ': ICorRuntimeHost:: GetDefaultDomain metodu hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::GetDefaultDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 53be5e3db7bec396743edc728942ad54efc0ec16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753828"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="d5f83-103">ICorRuntimeHost::GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5f83-103">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="d5f83-104"><xref:System._AppDomain?displayProperty=nameWithType>Geçerli işlem için varsayılan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-104">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5f83-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5f83-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5f83-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5f83-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d5f83-107">dışı <xref:System._AppDomain?displayProperty=nameWithType> <xref:System.AppDomain> İşlemin varsayılan uygulama etki alanını temsil eden örneğe türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d5f83-107">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="d5f83-108">Bu işaretçi yazıldığı `IUnknown` için, arayanların genellikle `QueryInterface` türünde bir arabirim işaretçisi almak için çağrı yapmaları gerekir <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d5f83-108">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5f83-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d5f83-109">Return Value</span></span>  
  
|<span data-ttu-id="d5f83-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5f83-110">HRESULT</span></span>|<span data-ttu-id="d5f83-111">Description</span><span class="sxs-lookup"><span data-stu-id="d5f83-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5f83-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5f83-112">S_OK</span></span>|<span data-ttu-id="d5f83-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d5f83-113">The operation was successful.</span></span>|  
|<span data-ttu-id="d5f83-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d5f83-114">S_FALSE</span></span>|<span data-ttu-id="d5f83-115">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="d5f83-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="d5f83-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5f83-116">E_FAIL</span></span>|<span data-ttu-id="d5f83-117">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d5f83-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d5f83-118">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d5f83-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d5f83-119">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5f83-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d5f83-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5f83-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5f83-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d5f83-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5f83-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5f83-122">Requirements</span></span>  

 <span data-ttu-id="d5f83-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5f83-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5f83-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5f83-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5f83-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d5f83-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5f83-126">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="d5f83-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f83-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5f83-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="d5f83-128">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5f83-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
