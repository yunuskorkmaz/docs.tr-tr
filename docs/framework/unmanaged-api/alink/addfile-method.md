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
ms.openlocfilehash: 7ff6bde5009e834bfca156fe4d3ad16da53ded85
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742389"
---
# <a name="addfile-method"></a><span data-ttu-id="3d6c2-102">AddFile Metodu</span><span class="sxs-lookup"><span data-stu-id="3d6c2-102">AddFile Method</span></span>
<span data-ttu-id="3d6c2-103">Dosyaları derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-103">Adds files to the assembly.</span></span> <span data-ttu-id="3d6c2-104">Ayrıca ilişkisiz modüller oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d6c2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d6c2-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d6c2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d6c2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3d6c2-107">Derleme genişletilmesi için benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="3d6c2-108">Eklenecek dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3d6c2-109">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="3d6c2-110">`dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="3d6c2-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="3d6c2-111">[Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) meta veriler yaymak için gerekiyorsa, kullanılacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="3d6c2-112">Eklenen dosyanın benzersiz kimliği depolanacağı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d6c2-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d6c2-113">Return Value</span></span>  
 <span data-ttu-id="3d6c2-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d6c2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d6c2-115">Requirements</span></span>  
 <span data-ttu-id="3d6c2-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6c2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-117">See also</span></span>

- [<span data-ttu-id="3d6c2-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d6c2-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3d6c2-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d6c2-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3d6c2-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="3d6c2-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
