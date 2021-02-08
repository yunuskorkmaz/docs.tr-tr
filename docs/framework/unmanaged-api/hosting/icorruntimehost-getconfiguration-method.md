---
description: ': ICorRuntimeHost:: GetConfiguration yöntemi hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::GetConfiguration Metodu
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: d3e3f065c3957fb29daa11ed7c46858a53865c91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784840"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="3985d-103">ICorRuntimeHost::GetConfiguration Metodu</span><span class="sxs-lookup"><span data-stu-id="3985d-103">ICorRuntimeHost::GetConfiguration Method</span></span>

<span data-ttu-id="3985d-104">Konağın ortak dil çalışma zamanının (CLR) geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="3985d-104">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3985d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3985d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3985d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3985d-106">Parameters</span></span>  

 `pConfiguration`  
 <span data-ttu-id="3985d-107">dışı CLR 'yi yapılandırmak için kullanılabilen [ICorConfiguration](icorconfiguration-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3985d-107">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3985d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3985d-108">Remarks</span></span>  

 <span data-ttu-id="3985d-109">CLR 'nin başlatılmasından önce yapılandırılması gerekir; Aksi takdirde, `GetConfiguration` Yöntem bir hata BELIRTEN hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="3985d-109">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3985d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3985d-110">Requirements</span></span>  

 <span data-ttu-id="3985d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3985d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3985d-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3985d-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3985d-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3985d-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3985d-114">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="3985d-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3985d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3985d-115">See also</span></span>

- [<span data-ttu-id="3985d-116">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3985d-116">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
