---
title: COUNINITIEE Numaralandırması
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dcd7dc7c51caa94308760c0086384c8eea184ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443603"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="73342-102">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="73342-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="73342-103">Tarafından kullanılan sabitlerini belirtir [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ortak dil çalışma zamanı başlatırken.</span><span class="sxs-lookup"><span data-stu-id="73342-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73342-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73342-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="73342-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="73342-105">Members</span></span>  
  
|<span data-ttu-id="73342-106">Üye</span><span class="sxs-lookup"><span data-stu-id="73342-106">Member</span></span>|<span data-ttu-id="73342-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73342-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="73342-108">Varsayılan başlatılmaması modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="73342-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="73342-109">Bir derlemeyi kaldırılması için başlatılmaması modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="73342-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73342-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73342-110">Requirements</span></span>  
 <span data-ttu-id="73342-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73342-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73342-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73342-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73342-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="73342-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73342-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73342-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73342-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73342-115">See Also</span></span>  
 [<span data-ttu-id="73342-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="73342-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
