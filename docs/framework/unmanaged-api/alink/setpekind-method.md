---
description: 'Daha fazla bilgi edinin: SetPEKind yöntemi'
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
ms.openlocfilehash: 4154e9e80b7f88b6951c9aa8da5fc23d340c96dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662305"
---
# <a name="setpekind-method"></a><span data-ttu-id="0b3d4-103">SetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b3d4-103">SetPEKind Method</span></span>

<span data-ttu-id="0b3d4-104">Taşınabilir yürütülebilir türü, makineye özgü veya makine belirsiz olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-104">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b3d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b3d4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="0b3d4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b3d4-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="0b3d4-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0b3d4-108">PE türü ayarlanacak dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-108">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="0b3d4-109">`AssemblyID`İlişkisiz bir netmodule BELIRTMEZSE null olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="0b3d4-110">[CorPEKind numaralandırması](../metadata/corpekind-enumeration.md)tarafından BELIRTILDIĞI gibi PE türü.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-110">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="0b3d4-111">NT üstbilgisinde gösterildiği gibi hedef makine mimarisi.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-111">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b3d4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b3d4-112">Return Value</span></span>  

 <span data-ttu-id="0b3d4-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b3d4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b3d4-114">Requirements</span></span>  

 <span data-ttu-id="0b3d4-115">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3d4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b3d4-116">See also</span></span>

- [<span data-ttu-id="0b3d4-117">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b3d4-117">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="0b3d4-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b3d4-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0b3d4-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b3d4-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0b3d4-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="0b3d4-120">ALink API</span></span>](index.md)
