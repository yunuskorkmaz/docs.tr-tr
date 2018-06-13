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
ms.openlocfilehash: 3c8864aa604b0483130eac5aa0d7c0640abbac99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443729"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="c2af0-102">CorFileMapping Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c2af0-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="c2af0-103">Çağrısından döndürülen dosya eşleme türünü tanımlayan değerleri içeren [Imetadataınfo::getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2af0-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2af0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2af0-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="c2af0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c2af0-105">Members</span></span>  
  
|<span data-ttu-id="c2af0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c2af0-106">Member</span></span>|<span data-ttu-id="c2af0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2af0-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="c2af0-108">Dosyayı bir veri dosyası olarak eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c2af0-108">The file is mapped as a data file.</span></span> <span data-ttu-id="c2af0-109">Diğer bir deyişle, `SEC_IMAGE` bayrağı değil Microsoft Win32'ye geçirildi `CreateFileMapping` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c2af0-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="c2af0-110">Dosyayı kullanarak yürütme için eşlenen `LoadLibrary` işlevi veya `CreateFileMapping` ile işlev `SEC_IMAGE` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="c2af0-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2af0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2af0-111">Requirements</span></span>  
 <span data-ttu-id="c2af0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2af0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2af0-113">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c2af0-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c2af0-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2af0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2af0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2af0-115">See Also</span></span>  
 [<span data-ttu-id="c2af0-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c2af0-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="c2af0-117">GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2af0-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
