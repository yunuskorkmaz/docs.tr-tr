---
title: CorRegFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7b935b8f59e434c9da364be1986dbed654a1efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445815"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="1a418-102">CorRegFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1a418-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="1a418-103">Kayıt için bir modül veya bileşik görüntü yüklenirken kullanılan bayrak değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a418-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a418-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a418-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="1a418-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1a418-105">Members</span></span>  
  
|<span data-ttu-id="1a418-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1a418-106">Member</span></span>|<span data-ttu-id="1a418-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a418-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="1a418-108">Dosyaları hedefe kopyalanmaması gereken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a418-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="1a418-109">Modül veya bileşik bir yapılandırma olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a418-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="1a418-110">Modül veya bileşik sınıf başvurularını olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a418-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a418-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a418-111">Requirements</span></span>  
 <span data-ttu-id="1a418-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a418-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a418-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a418-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a418-114">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1a418-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a418-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a418-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a418-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a418-116">See Also</span></span>  
 [<span data-ttu-id="1a418-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="1a418-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
