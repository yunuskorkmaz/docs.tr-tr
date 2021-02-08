---
description: 'Daha fazla bilgi edinin: CorFileMapping numaralandırması'
title: CorFileMapping Numaralandırması
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0fc3916e75c576a6b133ba8a49c00eec6c9bac19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784476"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="df75d-103">CorFileMapping Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="df75d-103">CorFileMapping Enumeration</span></span>

<span data-ttu-id="df75d-104">[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md) metoduna yapılan çağrıdan döndürülen dosya eşlemesinin türünü tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="df75d-104">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df75d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="df75d-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="df75d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="df75d-106">Members</span></span>  
  
|<span data-ttu-id="df75d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="df75d-107">Member</span></span>|<span data-ttu-id="df75d-108">Description</span><span class="sxs-lookup"><span data-stu-id="df75d-108">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="df75d-109">Dosya bir veri dosyası olarak eşlendi.</span><span class="sxs-lookup"><span data-stu-id="df75d-109">The file is mapped as a data file.</span></span> <span data-ttu-id="df75d-110">Yani, `SEC_IMAGE` bayrak Microsoft Win32 işlevine geçirilmedi `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="df75d-110">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="df75d-111">Dosya, bayrağı ile işlevi ya da işlevi kullanılarak yürütme için eşlenir `LoadLibrary` `CreateFileMapping` `SEC_IMAGE` .</span><span class="sxs-lookup"><span data-stu-id="df75d-111">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df75d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df75d-112">Requirements</span></span>  

 <span data-ttu-id="df75d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df75d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df75d-114">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="df75d-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="df75d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df75d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df75d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df75d-116">See also</span></span>

- [<span data-ttu-id="df75d-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="df75d-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="df75d-118">GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df75d-118">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
