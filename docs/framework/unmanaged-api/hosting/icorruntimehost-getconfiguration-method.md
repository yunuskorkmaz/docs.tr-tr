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
ms.openlocfilehash: 88abdbc62c8b27f48c5629afb99ab6e30ee67e00
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762272"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="4fa75-102">ICorRuntimeHost::GetConfiguration Metodu</span><span class="sxs-lookup"><span data-stu-id="4fa75-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="4fa75-103">Konağın ortak dil çalışma zamanının (CLR) geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="4fa75-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa75-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4fa75-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fa75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4fa75-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="4fa75-106">dışı CLR 'yi yapılandırmak için kullanılabilen [ICorConfiguration](icorconfiguration-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4fa75-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fa75-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fa75-107">Remarks</span></span>  
 <span data-ttu-id="4fa75-108">CLR 'nin başlatılmasından önce yapılandırılması gerekir; Aksi takdirde, `GetConfiguration` Yöntem bir hata BELIRTEN hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="4fa75-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa75-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fa75-109">Requirements</span></span>  
 <span data-ttu-id="4fa75-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fa75-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa75-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4fa75-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fa75-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4fa75-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fa75-113">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="4fa75-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa75-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa75-114">See also</span></span>

- [<span data-ttu-id="4fa75-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fa75-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
