---
title: "SetPEKind Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetPEKind
api_location: alink.dll
api_type: COM
f1_keywords: SetPEKind
helpviewer_keywords: SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d511bcda2ab4e879c123d866b3f6c887173c1d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="setpekind-method"></a><span data-ttu-id="345bf-102">SetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="345bf-102">SetPEKind Method</span></span>
<span data-ttu-id="345bf-103">Taşınabilir yürütülebilir türü, makine özgü veya makine belirsiz belirler.</span><span class="sxs-lookup"><span data-stu-id="345bf-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="345bf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="345bf-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="345bf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="345bf-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="345bf-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="345bf-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="345bf-107">PE türü ayarlanacak olduğu dosyasının belirteci.</span><span class="sxs-lookup"><span data-stu-id="345bf-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="345bf-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="345bf-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="345bf-109">Belirtildiği gibi PE türünü [CorPEKind numaralandırması](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="345bf-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="345bf-110">NT üstbilgisinde belirtildiği gibi hedef makine mimarisi.</span><span class="sxs-lookup"><span data-stu-id="345bf-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="345bf-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="345bf-111">Return Value</span></span>  
 <span data-ttu-id="345bf-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="345bf-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="345bf-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="345bf-113">Requirements</span></span>  
 <span data-ttu-id="345bf-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="345bf-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345bf-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="345bf-115">See Also</span></span>  
 [<span data-ttu-id="345bf-116">GetPEKind yöntemi</span><span class="sxs-lookup"><span data-stu-id="345bf-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="345bf-117">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="345bf-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="345bf-118">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="345bf-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="345bf-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="345bf-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
