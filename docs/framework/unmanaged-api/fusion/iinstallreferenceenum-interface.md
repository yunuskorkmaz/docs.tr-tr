---
title: IInstallReferenceEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum
helpviewer_keywords: IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3847d06c77a92eb6e63542f03405ca0cb9c9560
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="8d763-102">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d763-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="8d763-103">Genel derleme önbelleğinde yüklü başvurulan derlemeler için bir numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d763-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d763-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d763-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8d763-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8d763-105">Methods</span></span>  
  
|<span data-ttu-id="8d763-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8d763-106">Method</span></span>|<span data-ttu-id="8d763-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d763-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d763-108">Getnextınstallreferenceıtem yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d763-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="8d763-109">Bir işaretçi sonraki alır `IInstallReferenceItem` bu konuda yer alan `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="8d763-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d763-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d763-110">Requirements</span></span>  
 <span data-ttu-id="8d763-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d763-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d763-112">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8d763-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8d763-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d763-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d763-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d763-114">See Also</span></span>  
 [<span data-ttu-id="8d763-115">Fusion arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8d763-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="8d763-116">Iınstallreferenceıtem arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d763-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
