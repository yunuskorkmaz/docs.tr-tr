---
title: SetAssemblyFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ade568889d1c0203115f160d855de8c598798196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403363"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="c61ee-102">SetAssemblyFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c61ee-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="c61ee-103">Yeni bir derleme seçenekleri ve adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c61ee-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="c61ee-104">İlişkisiz modülleri üretmek olduğunda bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c61ee-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c61ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c61ee-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c61ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c61ee-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="c61ee-107">Bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="c61ee-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c61ee-108">[Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) bu dosya için arabirim.</span><span class="sxs-lookup"><span data-stu-id="c61ee-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="c61ee-109">Seçenekleri temsil ettiği [AssemblyFlags numaralandırması](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c61ee-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="c61ee-110">Yapılandırılan bir derleme için benzersiz kimlik alır.</span><span class="sxs-lookup"><span data-stu-id="c61ee-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c61ee-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c61ee-111">Return Value</span></span>  
 <span data-ttu-id="c61ee-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c61ee-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c61ee-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c61ee-113">Requirements</span></span>  
 <span data-ttu-id="c61ee-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c61ee-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61ee-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c61ee-115">See Also</span></span>  
 [<span data-ttu-id="c61ee-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c61ee-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c61ee-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c61ee-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c61ee-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="c61ee-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
