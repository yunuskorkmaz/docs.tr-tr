---
title: AddFile Method1
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84b68638ed0f7a86156cf7e5fcc98d3c02cba18a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662614"
---
# <a name="addfile-method1"></a><span data-ttu-id="e2cf7-102">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="e2cf7-102">AddFile Method1</span></span>
<span data-ttu-id="e2cf7-103">Dosyaları derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-103">Adds files to the assembly.</span></span> <span data-ttu-id="e2cf7-104">Ayrıca ilişkisiz modüller oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2cf7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2cf7-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2cf7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2cf7-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e2cf7-107">Derleme genişletilmesi için benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="e2cf7-108">Eklenecek dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e2cf7-109">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="e2cf7-110">`dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="e2cf7-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="e2cf7-111">[Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) meta veriler yaymak için gerekiyorsa, kullanılacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="e2cf7-112">Eklenen dosyanın benzersiz kimliği depolanacağı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2cf7-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2cf7-113">Return Value</span></span>  
 <span data-ttu-id="e2cf7-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2cf7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2cf7-115">Requirements</span></span>  
 <span data-ttu-id="e2cf7-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2cf7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2cf7-117">See also</span></span>
- [<span data-ttu-id="e2cf7-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2cf7-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e2cf7-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2cf7-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e2cf7-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="e2cf7-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
