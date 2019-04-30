---
title: AddFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a651be40773607e0db215eadf884ed642e6e3b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775674"
---
# <a name="addfile2-method"></a><span data-ttu-id="43ff1-102">AddFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43ff1-102">AddFile2 Method</span></span>
<span data-ttu-id="43ff1-103">Dosyaları derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="43ff1-103">Adds files to the assembly.</span></span> <span data-ttu-id="43ff1-104">Ayrıca ilişkisiz modüller oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43ff1-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ff1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43ff1-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="43ff1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43ff1-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="43ff1-107">Dosyanın ekleneceği derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="43ff1-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="43ff1-108">Eklenecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="43ff1-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="43ff1-109">COM + `FileDef` gibi bayrakları `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="43ff1-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="43ff1-110">`dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="43ff1-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="43ff1-111">Arabirimini [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="43ff1-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="43ff1-112">Eklenen dosya için kimliği alır.</span><span class="sxs-lookup"><span data-stu-id="43ff1-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43ff1-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43ff1-113">Return Value</span></span>  
 <span data-ttu-id="43ff1-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="43ff1-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ff1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43ff1-115">Requirements</span></span>  
 <span data-ttu-id="43ff1-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43ff1-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ff1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43ff1-117">See also</span></span>

- [<span data-ttu-id="43ff1-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43ff1-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="43ff1-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43ff1-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="43ff1-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="43ff1-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
