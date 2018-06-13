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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2997bb90f2d9034de398b901fcbd6265dcb59998
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430492"
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="47d81-102">CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="47d81-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="47d81-103">Özniteliklerini belirtir bir [Iassemblyname arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesi tarafından oluşturulduğunda [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="47d81-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47d81-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="47d81-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="47d81-105">Members</span></span>  
  
|<span data-ttu-id="47d81-106">Üye</span><span class="sxs-lookup"><span data-stu-id="47d81-106">Member</span></span>|<span data-ttu-id="47d81-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47d81-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="47d81-108">Geçirilen parametre değerinin metinsel bir kimlik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="47d81-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="47d81-109">Birkaç varsayılan değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="47d81-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="47d81-110">Arkadaş derleme kuralı (yalnızca ad ve ortak anahtar) doğrular.</span><span class="sxs-lookup"><span data-stu-id="47d81-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="47d81-111">Bu üye, yalnızca dahili kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="47d81-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="47d81-112">Bir birleşimini `CANOF_PARSE_DISPLAY_NAME` ve `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bayrakları.</span><span class="sxs-lookup"><span data-stu-id="47d81-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="47d81-113">Bu üye, yalnızca dahili kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="47d81-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47d81-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47d81-114">Requirements</span></span>  
 <span data-ttu-id="47d81-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47d81-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47d81-116">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="47d81-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="47d81-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47d81-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d81-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47d81-118">See Also</span></span>  
 [<span data-ttu-id="47d81-119">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47d81-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="47d81-120">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="47d81-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [<span data-ttu-id="47d81-121">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="47d81-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
