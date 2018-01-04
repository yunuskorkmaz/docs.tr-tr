---
title: "ImportTypes2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportTypes2
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes2
helpviewer_keywords: ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47c49253a1e2839939ef4e671f155e4a44d07529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="65558-102">ImportTypes2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65558-102">ImportTypes2 Method</span></span>
<span data-ttu-id="65558-103">Türleri alma işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="65558-103">Initiates the import of types.</span></span> <span data-ttu-id="65558-104">Üzerinden içe aktarılan her kapsamdan türleri almaya başlamak için bu yöntemi çağırın [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="65558-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65558-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65558-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65558-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65558-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="65558-107">İçeri aktarılacak derlemeye kimliği.</span><span class="sxs-lookup"><span data-stu-id="65558-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="65558-108">İçeri aktarmak için dosya kimliği.</span><span class="sxs-lookup"><span data-stu-id="65558-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="65558-109">Sıfır tabanlı kapsamı içeri aktarılacak.</span><span class="sxs-lookup"><span data-stu-id="65558-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="65558-110">Numaralandırıcı tanıtıcı türleri için verilen kapsam içinde alır.</span><span class="sxs-lookup"><span data-stu-id="65558-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="65558-111">İsteğe bağlı olarak alan [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="65558-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="65558-112">İsteğe bağlı olarak belirtilen kapsamında türleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="65558-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65558-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="65558-113">Return Value</span></span>  
 <span data-ttu-id="65558-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="65558-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65558-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65558-115">Requirements</span></span>  
 <span data-ttu-id="65558-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="65558-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65558-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65558-117">See Also</span></span>  
 [<span data-ttu-id="65558-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65558-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="65558-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65558-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="65558-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="65558-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
