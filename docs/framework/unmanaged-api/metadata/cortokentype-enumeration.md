---
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
ms.openlocfilehash: 629e18b6cd2fd7910804ecc608a45d2406dddea1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007500"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="21c91-102">CorTokenType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="21c91-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="21c91-103">Meta veri belirtecinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="21c91-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21c91-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="21c91-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="21c91-105">Members</span></span>  
  
|<span data-ttu-id="21c91-106">Üye</span><span class="sxs-lookup"><span data-stu-id="21c91-106">Member</span></span>|<span data-ttu-id="21c91-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21c91-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="21c91-108">`mdModule`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="21c91-109">`mdTypeRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="21c91-110">`mdTypeDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="21c91-111">`mdFieldDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="21c91-112">`mdMethodDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="21c91-113">`mdParamDef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="21c91-114">`mdInterfaceImpl`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="21c91-115">`mdMemberRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="21c91-116">`mdCustomAttribute`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="21c91-117">`mdPermission`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="21c91-118">`mdSignature`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="21c91-119">`mdEvent`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="21c91-120">`mdProperty`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="21c91-121">`mdModuleRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="21c91-122">`mdTypeSpec`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="21c91-123">`mdAssembly`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="21c91-124">`mdAssemblyRef`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="21c91-125">`mdFile`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="21c91-126">`mdExportedType`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="21c91-127">`mdManifestResource`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="21c91-128">`mdGenericParam`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="21c91-129">`mdMethodSpec`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="21c91-130">`mdGenericParamConstraint`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="21c91-131">`mdString`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="21c91-132">`mdName`Belirteç.</span><span class="sxs-lookup"><span data-stu-id="21c91-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="21c91-133">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="21c91-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21c91-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21c91-134">Remarks</span></span>  
 <span data-ttu-id="21c91-135">Her değer, karşılık gelen meta veri belirtecindeki en üstteki baytın değerine eşittir.</span><span class="sxs-lookup"><span data-stu-id="21c91-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21c91-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21c91-136">Requirements</span></span>  
 <span data-ttu-id="21c91-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21c91-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21c91-138">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="21c91-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="21c91-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21c91-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c91-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21c91-140">See also</span></span>

- [<span data-ttu-id="21c91-141">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="21c91-141">Metadata Enumerations</span></span>](metadata-enumerations.md)
