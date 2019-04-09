---
title: AddFile Metodu
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
ms.openlocfilehash: 056d1ac0ffd3ad7fa7cb1f86ae13331ac38b3eff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162221"
---
# <a name="addfile-method"></a><span data-ttu-id="d0624-102">AddFile Metodu</span><span class="sxs-lookup"><span data-stu-id="d0624-102">AddFile Method</span></span>
<span data-ttu-id="d0624-103">Dosyaları derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="d0624-103">Adds files to the assembly.</span></span> <span data-ttu-id="d0624-104">Ayrıca ilişkisiz modüller oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0624-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0624-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0624-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0624-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0624-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d0624-107">Derleme genişletilmesi için benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="d0624-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="d0624-108">Eklenecek dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="d0624-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d0624-109">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="d0624-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> `dwFlags` <span data-ttu-id="d0624-110">geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="d0624-110">is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="d0624-111">[Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) meta veriler yaymak için gerekiyorsa, kullanılacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d0624-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="d0624-112">Eklenen dosyanın benzersiz kimliği depolanacağı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0624-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0624-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0624-113">Return Value</span></span>  
 <span data-ttu-id="d0624-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0624-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0624-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0624-115">Requirements</span></span>  
 <span data-ttu-id="d0624-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0624-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0624-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0624-117">See also</span></span>

- [<span data-ttu-id="d0624-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0624-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d0624-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0624-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d0624-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="d0624-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
