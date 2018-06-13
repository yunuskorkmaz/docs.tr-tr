---
title: CreateInstallReferenceEnum İşlevi
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e35654b03f68a306329ef488289cfecd6f012484
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431580"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="600a9-102">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="600a9-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="600a9-103">Bir işaretçi alır bir [Iınstallreferenceenum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) belirtilen derleme uygulamanın başvurular listesini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="600a9-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="600a9-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="600a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="600a9-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="600a9-106">[out] Döndürülen `IInstallReferenceEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="600a9-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="600a9-107">[in] [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) derleme başvurularını numaralandırmak için için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="600a9-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="600a9-108">[in] Numaralandırıcının davranışını etkilemek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="600a9-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="600a9-109">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="600a9-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="600a9-110">`pvReserved` bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="600a9-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="600a9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="600a9-111">Requirements</span></span>  
 <span data-ttu-id="600a9-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="600a9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="600a9-113">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="600a9-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="600a9-114">**Kitaplığı:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="600a9-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="600a9-115">Fusion.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="600a9-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="600a9-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="600a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600a9-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="600a9-117">See Also</span></span>  
 [<span data-ttu-id="600a9-118">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="600a9-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [<span data-ttu-id="600a9-119">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="600a9-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="600a9-120">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="600a9-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
