---
title: SetAssemblyFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e557cc0da7bc684843ae3969242ffb84d811c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405352"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="b6ab3-102">SetAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6ab3-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="b6ab3-103">Oluşturulacak derlemenin adını atar.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="b6ab3-104">İlişkisiz modülleri üretirken amaçla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ab3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6ab3-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6ab3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6ab3-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="b6ab3-107">Bildirim dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="b6ab3-108">İşaretçi [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="b6ab3-109">Flags içinde tanımlanan [AssemblyFlags numaralandırması](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b6ab3-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="b6ab3-110">Sonuçta elde edilen derleme Kimliğini işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6ab3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6ab3-111">Return Value</span></span>  
 <span data-ttu-id="b6ab3-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ab3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6ab3-113">Requirements</span></span>  
 <span data-ttu-id="b6ab3-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ab3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6ab3-115">See Also</span></span>  
 [<span data-ttu-id="b6ab3-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6ab3-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b6ab3-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6ab3-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b6ab3-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="b6ab3-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
