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
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450299"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="a5f85-102">CorFileMapping Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a5f85-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="a5f85-103">[IMetaDataInfo:: GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metoduna yapılan çağrıdan döndürülen dosya eşlemesinin türünü tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a5f85-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5f85-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="a5f85-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="a5f85-105">Members</span></span>  
  
|<span data-ttu-id="a5f85-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="a5f85-106">Member</span></span>|<span data-ttu-id="a5f85-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5f85-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="a5f85-108">Dosya bir veri dosyası olarak eşlendi.</span><span class="sxs-lookup"><span data-stu-id="a5f85-108">The file is mapped as a data file.</span></span> <span data-ttu-id="a5f85-109">Diğer bir deyişle, `SEC_IMAGE` bayrağı Microsoft Win32 `CreateFileMapping` işlevine geçirilmedi.</span><span class="sxs-lookup"><span data-stu-id="a5f85-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="a5f85-110">Dosya, `SEC_IMAGE` bayrağıyla `LoadLibrary` işlevi ya da `CreateFileMapping` işlevi kullanılarak yürütme için eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a5f85-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5f85-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5f85-111">Requirements</span></span>  
 <span data-ttu-id="a5f85-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5f85-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5f85-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a5f85-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a5f85-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5f85-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f85-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f85-115">See also</span></span>

- [<span data-ttu-id="a5f85-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a5f85-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="a5f85-117">GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5f85-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
