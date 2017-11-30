---
title: "CreateInstallReferenceEnum İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateInstallReference
helpviewer_keywords: CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07c7ec72a66b37798e6e2af523bb024e9dd63d9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="b20b9-102">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="b20b9-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="b20b9-103">Bir işaretçi alır bir [Iınstallreferenceenum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) belirtilen derleme uygulamanın başvurular listesini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="b20b9-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b20b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b20b9-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b20b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b20b9-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="b20b9-106">[out] Döndürülen `IInstallReferenceEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b20b9-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="b20b9-107">[in] [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) derleme başvurularını numaralandırmak için için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b20b9-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b20b9-108">[in] Numaralandırıcının davranışını etkilemek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="b20b9-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="b20b9-109">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="b20b9-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b20b9-110">`pvReserved`bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b20b9-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b20b9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b20b9-111">Requirements</span></span>  
 <span data-ttu-id="b20b9-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b20b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b20b9-113">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b20b9-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b20b9-114">**Kitaplığı:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="b20b9-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="b20b9-115">Fusion.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b20b9-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b20b9-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b20b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b20b9-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b20b9-117">See Also</span></span>  
 [<span data-ttu-id="b20b9-118">Iınstallreferenceenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="b20b9-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [<span data-ttu-id="b20b9-119">Iassemblyname arabirimi</span><span class="sxs-lookup"><span data-stu-id="b20b9-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="b20b9-120">Fusion genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="b20b9-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
