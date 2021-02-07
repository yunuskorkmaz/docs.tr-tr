---
description: 'Hakkında daha fazla bilgi edinin: CREATE_ASM_NAME_OBJ_FLAGS numaralandırması'
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
ms.openlocfilehash: b68eed0671d57893e7ffbfbd8127c7ef872d5eb0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761206"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="32519-103">CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="32519-103">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>

<span data-ttu-id="32519-104">[CreateAssemblyNameObject](createassemblynameobject-function.md) işlevi tarafından oluşturulduğunda bir [IAssemblyName Interface](iassemblyname-interface.md) nesnesinin özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32519-104">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32519-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="32519-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="32519-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="32519-106">Members</span></span>  
  
|<span data-ttu-id="32519-107">Üye</span><span class="sxs-lookup"><span data-stu-id="32519-107">Member</span></span>|<span data-ttu-id="32519-108">Description</span><span class="sxs-lookup"><span data-stu-id="32519-108">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="32519-109">Geçirilen parametrenin bir metinsel kimlik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="32519-109">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="32519-110">Birkaç varsayılan değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="32519-110">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="32519-111">Arkadaş derleme kuralını doğrular (yalnızca ad ve ortak anahtar).</span><span class="sxs-lookup"><span data-stu-id="32519-111">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="32519-112">Bu üye yalnızca iç kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="32519-112">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="32519-113">`CANOF_PARSE_DISPLAY_NAME`And `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bayraklarının birleşimi.</span><span class="sxs-lookup"><span data-stu-id="32519-113">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="32519-114">Bu üye yalnızca iç kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="32519-114">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32519-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32519-115">Requirements</span></span>  

 <span data-ttu-id="32519-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32519-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32519-117">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="32519-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="32519-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32519-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32519-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32519-119">See also</span></span>

- [<span data-ttu-id="32519-120">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32519-120">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="32519-121">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="32519-121">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="32519-122">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="32519-122">Fusion Enumerations</span></span>](fusion-enumerations.md)
