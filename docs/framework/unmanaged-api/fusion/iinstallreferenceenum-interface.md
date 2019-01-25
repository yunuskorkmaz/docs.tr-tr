---
title: IInstallReferenceEnum Arabirimi
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2aed89008dd2fa86b38f243c8e7cca1bdda901e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497780"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="3571e-102">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3571e-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="3571e-103">Genel derleme önbelleğinde yüklü başvurulan derlemeler için bir numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3571e-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3571e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3571e-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3571e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3571e-105">Methods</span></span>  
  
|<span data-ttu-id="3571e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3571e-106">Method</span></span>|<span data-ttu-id="3571e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3571e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3571e-108">GetNextInstallReferenceItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3571e-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="3571e-109">Sonraki bir işaretçi alır `IInstallReferenceItem` bu konuda yer alan `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="3571e-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3571e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3571e-110">Requirements</span></span>  
 <span data-ttu-id="3571e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3571e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3571e-112">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3571e-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3571e-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3571e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3571e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3571e-114">See also</span></span>
- [<span data-ttu-id="3571e-115">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3571e-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="3571e-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3571e-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
