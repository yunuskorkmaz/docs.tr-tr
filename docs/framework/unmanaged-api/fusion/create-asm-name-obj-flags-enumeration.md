---
title: CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: 52d5ad3a18c102422e90621c7d1e23b2692c0000
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683244"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="f9dc2-102">CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f9dc2-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>

<span data-ttu-id="f9dc2-103">[CreateAssemblyNameObject](createassemblynameobject-function.md) işlevi tarafından oluşturulduğunda bir [IAssemblyName Interface](iassemblyname-interface.md) nesnesinin özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9dc2-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9dc2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9dc2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="f9dc2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f9dc2-105">Members</span></span>  
  
|<span data-ttu-id="f9dc2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f9dc2-106">Member</span></span>|<span data-ttu-id="f9dc2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9dc2-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="f9dc2-108">Geçirilen parametrenin bir metinsel kimlik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9dc2-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="f9dc2-109">Birkaç varsayılan değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f9dc2-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="f9dc2-110">Arkadaş derleme kuralını doğrular (yalnızca ad ve ortak anahtar).</span><span class="sxs-lookup"><span data-stu-id="f9dc2-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="f9dc2-111">Bu üye yalnızca iç kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="f9dc2-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="f9dc2-112">`CANOF_PARSE_DISPLAY_NAME`And `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bayraklarının birleşimi.</span><span class="sxs-lookup"><span data-stu-id="f9dc2-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="f9dc2-113">Bu üye yalnızca iç kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="f9dc2-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9dc2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9dc2-114">Requirements</span></span>  

 <span data-ttu-id="f9dc2-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9dc2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9dc2-116">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f9dc2-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f9dc2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9dc2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9dc2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9dc2-118">See also</span></span>

- [<span data-ttu-id="f9dc2-119">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9dc2-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f9dc2-120">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="f9dc2-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="f9dc2-121">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f9dc2-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
