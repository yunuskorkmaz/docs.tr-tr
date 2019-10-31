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
ms.openlocfilehash: d3f7c24b4bd373924c44dbc0490c890e7f1322bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131726"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="cfa8b-102">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa8b-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="cfa8b-103">Genel derleme önbelleğinde yüklü olan başvurulan derlemeler için bir Numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cfa8b-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa8b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfa8b-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cfa8b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cfa8b-105">Methods</span></span>  
  
|<span data-ttu-id="cfa8b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cfa8b-106">Method</span></span>|<span data-ttu-id="cfa8b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfa8b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfa8b-108">GetNextInstallReferenceItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfa8b-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="cfa8b-109">Bu `IInstallReferenceEnum`bulunan bir sonraki `IInstallReferenceItem` yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="cfa8b-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cfa8b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfa8b-110">Requirements</span></span>  
 <span data-ttu-id="cfa8b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfa8b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa8b-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="cfa8b-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cfa8b-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfa8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa8b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa8b-114">See also</span></span>

- [<span data-ttu-id="cfa8b-115">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cfa8b-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="cfa8b-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa8b-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
