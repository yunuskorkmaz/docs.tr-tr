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
ms.openlocfilehash: a19762cbec91871d7af617957896e4ee34944fba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132723"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="b69d8-102">SetAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b69d8-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="b69d8-103">Oluşturulacak derlemenin adını atar.</span><span class="sxs-lookup"><span data-stu-id="b69d8-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="b69d8-104">İlişkisiz modülleri üretirken amaçla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b69d8-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b69d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b69d8-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b69d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b69d8-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="b69d8-107">Bildirim dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="b69d8-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="b69d8-108">İşaretçi [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b69d8-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="b69d8-109">Bayrakları sınıfında tanımlandığı gibi [AssemblyFlags numaralandırması](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b69d8-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="b69d8-110">Oluşturulan derleme kimliği için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b69d8-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b69d8-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b69d8-111">Return Value</span></span>  
 <span data-ttu-id="b69d8-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b69d8-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b69d8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b69d8-113">Requirements</span></span>  
 <span data-ttu-id="b69d8-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b69d8-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b69d8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b69d8-115">See also</span></span>

- [<span data-ttu-id="b69d8-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b69d8-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b69d8-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b69d8-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b69d8-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="b69d8-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
