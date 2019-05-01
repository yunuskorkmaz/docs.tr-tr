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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b33b50e53c454f2b62253d12943ea044240d8cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045207"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="915d4-102">CorTokenType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="915d4-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="915d4-103">Meta veri belirteci türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="915d4-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="915d4-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="915d4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="915d4-105">Members</span></span>  
  
|<span data-ttu-id="915d4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="915d4-106">Member</span></span>|<span data-ttu-id="915d4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="915d4-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="915d4-108">Bir `mdModule` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="915d4-109">Bir `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="915d4-110">Bir `mdTypeDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="915d4-111">Bir `mdFieldDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="915d4-112">Bir `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="915d4-113">Bir `mdParamDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="915d4-114">Bir `mdInterfaceImpl` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="915d4-115">Bir `mdMemberRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="915d4-116">Bir `mdCustomAttribute` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="915d4-117">Bir `mdPermission` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="915d4-118">Bir `mdSignature` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="915d4-119">Bir `mdEvent` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="915d4-120">Bir `mdProperty` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="915d4-121">Bir `mdModuleRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="915d4-122">Bir `mdTypeSpec` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="915d4-123">Bir `mdAssembly` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="915d4-124">Bir `mdAssemblyRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="915d4-125">Bir `mdFile` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="915d4-126">Bir `mdExportedType` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="915d4-127">Bir `mdManifestResource` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="915d4-128">Bir `mdGenericParam` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="915d4-129">Bir `mdMethodSpec` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="915d4-130">Bir `mdGenericParamConstraint` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="915d4-131">Bir `mdString` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="915d4-132">Bir `mdName` belirteci.</span><span class="sxs-lookup"><span data-stu-id="915d4-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="915d4-133">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="915d4-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="915d4-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="915d4-134">Remarks</span></span>  
 <span data-ttu-id="915d4-135">Her değer karşılık gelen meta veri belirteci üstteki bayt değerine eşittir.</span><span class="sxs-lookup"><span data-stu-id="915d4-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915d4-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="915d4-136">Requirements</span></span>  
 <span data-ttu-id="915d4-137">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="915d4-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="915d4-138">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="915d4-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="915d4-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="915d4-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915d4-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="915d4-140">See also</span></span>

- [<span data-ttu-id="915d4-141">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="915d4-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
