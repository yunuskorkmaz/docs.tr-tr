---
title: ImportFile Metodu
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: cda6d90865f8ad2b9d565f6a6378c35b03c65bf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446998"
---
# <a name="importfile-method"></a><span data-ttu-id="48c46-102">ImportFile Metodu</span><span class="sxs-lookup"><span data-stu-id="48c46-102">ImportFile Method</span></span>
<span data-ttu-id="48c46-103">Imports assemblies and unbound modules.</span><span class="sxs-lookup"><span data-stu-id="48c46-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48c46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48c46-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="48c46-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48c46-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="48c46-106">Fully qualified name of file to be imported.</span><span class="sxs-lookup"><span data-stu-id="48c46-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="48c46-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span><span class="sxs-lookup"><span data-stu-id="48c46-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="48c46-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span><span class="sxs-lookup"><span data-stu-id="48c46-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="48c46-109">Pointer to token where a unique file ID will be stored.</span><span class="sxs-lookup"><span data-stu-id="48c46-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="48c46-110">The file can be an assembly or a file.</span><span class="sxs-lookup"><span data-stu-id="48c46-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="48c46-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="48c46-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="48c46-112">Can be NULL if the file is not an assembly.</span><span class="sxs-lookup"><span data-stu-id="48c46-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="48c46-113">Pointer to the count of files and/or scopes that have been imported.</span><span class="sxs-lookup"><span data-stu-id="48c46-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48c46-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="48c46-114">Return Value</span></span>  
 <span data-ttu-id="48c46-115">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="48c46-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48c46-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48c46-116">Requirements</span></span>  
 <span data-ttu-id="48c46-117">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="48c46-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c46-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48c46-118">See also</span></span>

- [<span data-ttu-id="48c46-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48c46-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="48c46-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48c46-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="48c46-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="48c46-121">ALink API</span></span>](index.md)
