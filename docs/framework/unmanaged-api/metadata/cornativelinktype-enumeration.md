---
title: CorNativeLinkType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: 0b613ebacdff82a29fdbc3f4caa0f2b8bb5d3f6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176168"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="04e9e-102">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="04e9e-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="04e9e-103">Yerel koda bağlı türü gösteren değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="04e9e-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04e9e-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="04e9e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="04e9e-105">Members</span></span>  
  
|<span data-ttu-id="04e9e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="04e9e-106">Member</span></span>|<span data-ttu-id="04e9e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04e9e-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="04e9e-108">Anahtar kelimelerden hiçbirinin belirtilmemiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="04e9e-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="04e9e-109">ANSI anahtar kelimesinin belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="04e9e-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="04e9e-110">Unicode anahtar kelimesinin belirtildiğini gösterir</span><span class="sxs-lookup"><span data-stu-id="04e9e-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="04e9e-111">Otomatik anahtar kelimenin belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="04e9e-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="04e9e-112">OLE anahtar kelimesinin belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="04e9e-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="04e9e-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="04e9e-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04e9e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04e9e-114">Requirements</span></span>  
 <span data-ttu-id="04e9e-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e9e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e9e-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04e9e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04e9e-117">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="04e9e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04e9e-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e9e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e9e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04e9e-119">See also</span></span>

- [<span data-ttu-id="04e9e-120">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="04e9e-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
