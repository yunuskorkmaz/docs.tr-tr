---
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
ms.openlocfilehash: 2a50814a67be5a01a7413050683a915355665f3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720652"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="aae79-102">ICorRuntimeHost::GetConfiguration Metodu</span><span class="sxs-lookup"><span data-stu-id="aae79-102">ICorRuntimeHost::GetConfiguration Method</span></span>

<span data-ttu-id="aae79-103">Konağın ortak dil çalışma zamanının (CLR) geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="aae79-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae79-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aae79-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aae79-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aae79-105">Parameters</span></span>  

 `pConfiguration`  
 <span data-ttu-id="aae79-106">dışı CLR 'yi yapılandırmak için kullanılabilen [ICorConfiguration](icorconfiguration-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aae79-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aae79-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aae79-107">Remarks</span></span>  

 <span data-ttu-id="aae79-108">CLR 'nin başlatılmasından önce yapılandırılması gerekir; Aksi takdirde, `GetConfiguration` Yöntem bir hata BELIRTEN hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="aae79-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aae79-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aae79-109">Requirements</span></span>  

 <span data-ttu-id="aae79-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aae79-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae79-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aae79-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aae79-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="aae79-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aae79-113">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="aae79-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae79-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aae79-114">See also</span></span>

- [<span data-ttu-id="aae79-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aae79-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
