---
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
ms.openlocfilehash: 63e27a62e176a92b03c10b59a55d9da3192918f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726124"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="021f3-102">CorFileMapping Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="021f3-102">CorFileMapping Enumeration</span></span>

<span data-ttu-id="021f3-103">[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md) metoduna yapılan çağrıdan döndürülen dosya eşlemesinin türünü tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="021f3-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="021f3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="021f3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="021f3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="021f3-105">Members</span></span>  
  
|<span data-ttu-id="021f3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="021f3-106">Member</span></span>|<span data-ttu-id="021f3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="021f3-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="021f3-108">Dosya bir veri dosyası olarak eşlendi.</span><span class="sxs-lookup"><span data-stu-id="021f3-108">The file is mapped as a data file.</span></span> <span data-ttu-id="021f3-109">Yani, `SEC_IMAGE` bayrak Microsoft Win32 işlevine geçirilmedi `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="021f3-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="021f3-110">Dosya, bayrağı ile işlevi ya da işlevi kullanılarak yürütme için eşlenir `LoadLibrary` `CreateFileMapping` `SEC_IMAGE` .</span><span class="sxs-lookup"><span data-stu-id="021f3-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="021f3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="021f3-111">Requirements</span></span>  

 <span data-ttu-id="021f3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="021f3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="021f3-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="021f3-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="021f3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="021f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="021f3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="021f3-115">See also</span></span>

- [<span data-ttu-id="021f3-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="021f3-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="021f3-117">GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="021f3-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
