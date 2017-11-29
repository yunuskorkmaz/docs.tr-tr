---
title: AddFile Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.AddFile
- AddFile
api_location: alink.dll
api_type: COM
f1_keywords: AddFile
helpviewer_keywords: AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9463f2c41f56287ebfc4fb55aa8208c37522a57f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addfile-method1"></a><span data-ttu-id="707e2-102">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="707e2-102">AddFile Method1</span></span>
<span data-ttu-id="707e2-103">Dosyaları derlemeye ekler.</span><span class="sxs-lookup"><span data-stu-id="707e2-103">Adds files to the assembly.</span></span> <span data-ttu-id="707e2-104">Ayrıca ilişkisiz modülleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="707e2-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="707e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="707e2-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="707e2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="707e2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="707e2-107">Derleme engagement'ta benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="707e2-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="707e2-108">Eklenecek dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="707e2-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="707e2-109">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="707e2-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="707e2-110">`dwFlags`geçirilir [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="707e2-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="707e2-111">[Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) meta verileri, yayma gerekiyorsa, kullanılacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="707e2-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="707e2-112">Eklenen dosyanın benzersiz Kimliğini depolanacağı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="707e2-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="707e2-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="707e2-113">Return Value</span></span>  
 <span data-ttu-id="707e2-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="707e2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707e2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="707e2-115">Requirements</span></span>  
 <span data-ttu-id="707e2-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="707e2-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707e2-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="707e2-117">See Also</span></span>  
 [<span data-ttu-id="707e2-118">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="707e2-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="707e2-119">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="707e2-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="707e2-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="707e2-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
