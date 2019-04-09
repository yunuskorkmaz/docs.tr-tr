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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3056836d289383161f9fa538c3c6349f88b6ba6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175623"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="d9031-102">CorFileMapping Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d9031-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="d9031-103">Çağrısından döndürülen dosya eşlemesi türünü tanımlayan değerleri içeren [Imetadataınfo::getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d9031-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9031-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9031-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="d9031-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d9031-105">Members</span></span>  
  
|<span data-ttu-id="d9031-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d9031-106">Member</span></span>|<span data-ttu-id="d9031-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9031-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="d9031-108">Dosyayı bir veri dosyası olarak eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d9031-108">The file is mapped as a data file.</span></span> <span data-ttu-id="d9031-109">Diğer bir deyişle, `SEC_IMAGE` bayrağı değil Microsoft Win32 öğesine geçirildi `CreateFileMapping` işlevi.</span><span class="sxs-lookup"><span data-stu-id="d9031-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="d9031-110">Dosyayı kullanarak yürütme için eşlenmiş `LoadLibrary` işlevi veya `CreateFileMapping` işleviyle `SEC_IMAGE` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="d9031-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9031-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9031-111">Requirements</span></span>  
 <span data-ttu-id="d9031-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9031-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9031-113">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d9031-113">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="d9031-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d9031-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9031-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9031-115">See also</span></span>

- [<span data-ttu-id="d9031-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d9031-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="d9031-117">GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9031-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
