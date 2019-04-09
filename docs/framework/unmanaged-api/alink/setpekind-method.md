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
ms.openlocfilehash: dec04fa267c61798a3340e9d1e18150b812e9eaf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092662"
---
# <a name="setpekind-method"></a><span data-ttu-id="aff5f-102">SetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aff5f-102">SetPEKind Method</span></span>
<span data-ttu-id="aff5f-103">Taşınabilir yürütülebilir türü, makineye özgü veya makine geçişte sorun yaşamaz belirler.</span><span class="sxs-lookup"><span data-stu-id="aff5f-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff5f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aff5f-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="aff5f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aff5f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="aff5f-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="aff5f-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="aff5f-107">Dosyanın PE türü ayarlanacak olduğu belirteci.</span><span class="sxs-lookup"><span data-stu-id="aff5f-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="aff5f-108">NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="aff5f-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="aff5f-109">Türü tarafından belirtildiği şekilde PE [CorPEKind numaralandırması](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="aff5f-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="aff5f-110">NT başlığında belirtildiği gibi hedef makine mimarisi.</span><span class="sxs-lookup"><span data-stu-id="aff5f-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aff5f-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aff5f-111">Return Value</span></span>  
 <span data-ttu-id="aff5f-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="aff5f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff5f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aff5f-113">Requirements</span></span>  
 <span data-ttu-id="aff5f-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="aff5f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff5f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aff5f-115">See also</span></span>

- [<span data-ttu-id="aff5f-116">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aff5f-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="aff5f-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aff5f-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="aff5f-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aff5f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="aff5f-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="aff5f-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
