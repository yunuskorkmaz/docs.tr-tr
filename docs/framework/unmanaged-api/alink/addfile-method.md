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
ms.workload: dotnet
ms.openlocfilehash: 943ff2901ee0888860941e86d589060de729907d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="addfile-method1"></a><span data-ttu-id="2a844-102">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="2a844-102">AddFile Method1</span></span>
<span data-ttu-id="2a844-103">Dosyaları derlemeye ekler.</span><span class="sxs-lookup"><span data-stu-id="2a844-103">Adds files to the assembly.</span></span> <span data-ttu-id="2a844-104">Ayrıca ilişkisiz modülleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a844-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a844-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a844-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a844-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a844-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2a844-107">Derleme engagement'ta benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="2a844-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="2a844-108">Eklenecek dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="2a844-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2a844-109">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="2a844-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="2a844-110">`dwFlags`geçirilir [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="2a844-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="2a844-111">[Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) meta verileri, yayma gerekiyorsa, kullanılacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2a844-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="2a844-112">Eklenen dosyanın benzersiz Kimliğini depolanacağı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2a844-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a844-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2a844-113">Return Value</span></span>  
 <span data-ttu-id="2a844-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a844-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a844-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a844-115">Requirements</span></span>  
 <span data-ttu-id="2a844-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2a844-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a844-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a844-117">See Also</span></span>  
 [<span data-ttu-id="2a844-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a844-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2a844-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a844-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2a844-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="2a844-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
