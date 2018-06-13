---
title: CorLinkerOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d154985e9c1614e6b8f13a55410ead0cb5e861b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441061"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="5f593-102">CorLinkerOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5f593-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="5f593-103">Meta veri bağlayıcı seçeneklerini seçmek için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f593-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f593-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f593-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="5f593-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5f593-105">Members</span></span>  
  
|<span data-ttu-id="5f593-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5f593-106">Member</span></span>|<span data-ttu-id="5f593-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f593-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="5f593-108">Özel türler ve genel işlevler korunmaz.</span><span class="sxs-lookup"><span data-stu-id="5f593-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="5f593-109">Özel türler ve genel işlevler korunur.</span><span class="sxs-lookup"><span data-stu-id="5f593-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f593-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f593-110">Requirements</span></span>  
 <span data-ttu-id="5f593-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f593-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f593-112">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5f593-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5f593-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f593-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f593-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f593-114">See Also</span></span>  
 [<span data-ttu-id="5f593-115">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5f593-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
