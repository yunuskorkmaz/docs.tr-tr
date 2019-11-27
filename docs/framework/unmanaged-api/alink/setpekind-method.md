---
title: SetPEKind Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: dfbc10bdbe633450dee2e27524c29ead21fb739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445540"
---
# <a name="setpekind-method"></a><span data-ttu-id="e5270-102">SetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5270-102">SetPEKind Method</span></span>
<span data-ttu-id="e5270-103">Taşınabilir yürütülebilir türü, makineye özgü veya makine belirsiz olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="e5270-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5270-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5270-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="e5270-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5270-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e5270-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e5270-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e5270-107">PE türü ayarlanacak dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="e5270-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="e5270-108">`AssemblyID` ilişkisiz bir netmodule belirtmezse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5270-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="e5270-109">[CorPEKind numaralandırması](../metadata/corpekind-enumeration.md)tarafından BELIRTILDIĞI gibi PE türü.</span><span class="sxs-lookup"><span data-stu-id="e5270-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="e5270-110">NT üstbilgisinde gösterildiği gibi hedef makine mimarisi.</span><span class="sxs-lookup"><span data-stu-id="e5270-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5270-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e5270-111">Return Value</span></span>  
 <span data-ttu-id="e5270-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5270-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5270-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5270-113">Requirements</span></span>  
 <span data-ttu-id="e5270-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5270-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5270-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5270-115">See also</span></span>

- [<span data-ttu-id="e5270-116">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5270-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="e5270-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5270-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e5270-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5270-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e5270-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="e5270-119">ALink API</span></span>](index.md)
