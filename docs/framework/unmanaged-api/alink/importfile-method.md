---
title: "ImportFile Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46830699ba43c406da313653e1910e8f7a18a2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="importfile-method"></a><span data-ttu-id="75c6d-102">ImportFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75c6d-102">ImportFile Method</span></span>
<span data-ttu-id="75c6d-103">Derlemeler ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="75c6d-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75c6d-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75c6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75c6d-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="75c6d-106">İçeri aktarılacak dosya tam adı.</span><span class="sxs-lookup"><span data-stu-id="75c6d-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="75c6d-107">Derlemeye bağlı olarak dosyayı yeniden adlandırmak için kullanılan isteğe bağlı çıktı dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="75c6d-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="75c6d-108">TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75c6d-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="75c6d-109">Benzersiz dosya kimliği depolanacağı belirtecine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75c6d-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="75c6d-110">Dosya, bir derlemeyi ya da bir dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="75c6d-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="75c6d-111">İşaretçi alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="75c6d-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="75c6d-112">Dosya bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="75c6d-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="75c6d-113">Dosyaları ve/veya içeri aktarıldığını kapsamların sayısı işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75c6d-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75c6d-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="75c6d-114">Return Value</span></span>  
 <span data-ttu-id="75c6d-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="75c6d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75c6d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75c6d-116">Requirements</span></span>  
 <span data-ttu-id="75c6d-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="75c6d-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c6d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75c6d-118">See Also</span></span>  
 [<span data-ttu-id="75c6d-119">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="75c6d-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="75c6d-120">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="75c6d-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="75c6d-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="75c6d-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
