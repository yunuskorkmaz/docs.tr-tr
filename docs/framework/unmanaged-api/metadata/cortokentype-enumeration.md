---
description: 'Daha fazla bilgi edinin: CorTokenType numaralandırması'
title: CorTokenType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 954bddccd8fe20be46080f8843bcf754e0cf1bbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678412"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="9d8a7-103">CorTokenType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9d8a7-103">CorTokenType Enumeration</span></span>

<span data-ttu-id="9d8a7-104">Meta veri belirtecinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-104">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d8a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d8a7-105">Syntax</span></span>  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="9d8a7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9d8a7-106">Members</span></span>  
  
|<span data-ttu-id="9d8a7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="9d8a7-107">Member</span></span>|<span data-ttu-id="9d8a7-108">Description</span><span class="sxs-lookup"><span data-stu-id="9d8a7-108">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="9d8a7-109">`mdModule`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-109">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="9d8a7-110">`mdTypeRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-110">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="9d8a7-111">`mdTypeDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-111">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="9d8a7-112">`mdFieldDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-112">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="9d8a7-113">`mdMethodDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-113">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="9d8a7-114">`mdParamDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-114">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="9d8a7-115">`mdInterfaceImpl`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-115">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="9d8a7-116">`mdMemberRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-116">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="9d8a7-117">`mdCustomAttribute`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-117">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="9d8a7-118">`mdPermission`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-118">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="9d8a7-119">`mdSignature`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-119">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="9d8a7-120">`mdEvent`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-120">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="9d8a7-121">`mdProperty`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-121">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="9d8a7-122">`mdModuleRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-122">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="9d8a7-123">`mdTypeSpec`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-123">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="9d8a7-124">`mdAssembly`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-124">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="9d8a7-125">`mdAssemblyRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-125">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="9d8a7-126">`mdFile`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-126">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="9d8a7-127">`mdExportedType`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-127">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="9d8a7-128">`mdManifestResource`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-128">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="9d8a7-129">`mdGenericParam`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-129">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="9d8a7-130">`mdMethodSpec`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-130">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="9d8a7-131">`mdGenericParamConstraint`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-131">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="9d8a7-132">`mdString`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-132">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="9d8a7-133">`mdName`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-133">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="9d8a7-134">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-134">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d8a7-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d8a7-135">Remarks</span></span>  

 <span data-ttu-id="9d8a7-136">Her değer, karşılık gelen meta veri belirtecindeki en üstteki baytın değerine eşittir.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-136">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d8a7-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d8a7-137">Requirements</span></span>  

 <span data-ttu-id="9d8a7-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d8a7-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d8a7-139">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="9d8a7-139">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9d8a7-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d8a7-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8a7-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d8a7-141">See also</span></span>

- [<span data-ttu-id="9d8a7-142">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="9d8a7-142">Metadata Enumerations</span></span>](metadata-enumerations.md)
