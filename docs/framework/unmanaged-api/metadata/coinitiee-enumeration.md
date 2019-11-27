---
title: COINITIEE Numaralandırması
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444109"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="8e857-102">COINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8e857-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="8e857-103">Ortak dil çalışma zamanı başlatılırken [Coınitialeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) tarafından kullanılan sabitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e857-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e857-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e857-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="8e857-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="8e857-105">Members</span></span>  
  
|<span data-ttu-id="8e857-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="8e857-106">Member</span></span>|<span data-ttu-id="8e857-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e857-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="8e857-108">Varsayılan başlatma modu.</span><span class="sxs-lookup"><span data-stu-id="8e857-108">Default initialization mode.</span></span> <span data-ttu-id="8e857-109">Bu, çalışma zamanını başlatır ve varsayılan <xref:System.AppDomain>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8e857-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="8e857-110">Yönetilen DLL çalıştırmak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="8e857-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="8e857-111">Yönetilen bir EXE çalıştırmak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="8e857-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="8e857-112">Bu, çalışma zamanını başlatır, ancak varsayılan <xref:System.AppDomain>oluşturmaz ve bu, EXE 'nin ana yordamına girdikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8e857-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e857-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e857-113">Requirements</span></span>  
 <span data-ttu-id="8e857-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e857-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e857-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8e857-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e857-116">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8e857-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e857-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e857-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e857-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e857-118">See also</span></span>

- [<span data-ttu-id="8e857-119">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8e857-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
