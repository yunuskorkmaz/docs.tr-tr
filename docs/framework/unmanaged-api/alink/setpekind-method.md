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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b985aeb97621e552e9e97581e67cae029d019ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405899"
---
# <a name="setpekind-method"></a><span data-ttu-id="51542-102">SetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51542-102">SetPEKind Method</span></span>
<span data-ttu-id="51542-103">Taşınabilir yürütülebilir türü, makine özgü veya makine belirsiz belirler.</span><span class="sxs-lookup"><span data-stu-id="51542-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51542-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51542-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="51542-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51542-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="51542-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="51542-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="51542-107">PE türü ayarlanacak olduğu dosyasının belirteci.</span><span class="sxs-lookup"><span data-stu-id="51542-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="51542-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="51542-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="51542-109">Belirtildiği gibi PE türünü [CorPEKind numaralandırması](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="51542-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="51542-110">NT üstbilgisinde belirtildiği gibi hedef makine mimarisi.</span><span class="sxs-lookup"><span data-stu-id="51542-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51542-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="51542-111">Return Value</span></span>  
 <span data-ttu-id="51542-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="51542-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51542-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51542-113">Requirements</span></span>  
 <span data-ttu-id="51542-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="51542-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51542-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51542-115">See Also</span></span>  
 [<span data-ttu-id="51542-116">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51542-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="51542-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51542-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="51542-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51542-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="51542-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="51542-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
