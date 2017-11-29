---
title: "AddFile2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddFile2
- IALink2.AddFile2
api_location: alink.dll
api_type: COM
f1_keywords: AddFile2
helpviewer_keywords: AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe10a3ca8930087a52d02905534696dbb2d8fb25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addfile2-method"></a><span data-ttu-id="444fe-102">AddFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="444fe-102">AddFile2 Method</span></span>
<span data-ttu-id="444fe-103">Dosyaları derlemeye ekler.</span><span class="sxs-lookup"><span data-stu-id="444fe-103">Adds files to the assembly.</span></span> <span data-ttu-id="444fe-104">Ayrıca ilişkisiz modülleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="444fe-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="444fe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="444fe-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="444fe-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="444fe-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="444fe-107">Dosya ekleneceği derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="444fe-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="444fe-108">Eklenecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="444fe-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="444fe-109">COM + `FileDef` gibi bayrakları `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="444fe-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="444fe-110">`dwFlags`geçirilir [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="444fe-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="444fe-111">Arabirimini [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="444fe-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="444fe-112">Eklenen dosyanın kimliği alır.</span><span class="sxs-lookup"><span data-stu-id="444fe-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="444fe-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="444fe-113">Return Value</span></span>  
 <span data-ttu-id="444fe-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="444fe-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="444fe-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="444fe-115">Requirements</span></span>  
 <span data-ttu-id="444fe-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="444fe-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444fe-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="444fe-117">See Also</span></span>  
 [<span data-ttu-id="444fe-118">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="444fe-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="444fe-119">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="444fe-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="444fe-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="444fe-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
