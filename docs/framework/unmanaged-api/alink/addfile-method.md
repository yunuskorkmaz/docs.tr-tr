---
title: AddFile Yöntemi
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
ms.openlocfilehash: c04bc008d0279601e90d13e6a57c52a458fca1d7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967886"
---
# <a name="addfile-method"></a><span data-ttu-id="a7965-102">AddFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7965-102">AddFile Method</span></span>
<span data-ttu-id="a7965-103">Dosyaları derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="a7965-103">Adds files to the assembly.</span></span> <span data-ttu-id="a7965-104">Ayrıca ilişkisiz modüller oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7965-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7965-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7965-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7965-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7965-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a7965-107">Derleme genişletilmesi için benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="a7965-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="a7965-108">Eklenecek dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="a7965-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a7965-109">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="a7965-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="a7965-110">`dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a7965-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="a7965-111">[Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) meta veriler yaymak için gerekiyorsa, kullanılacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a7965-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="a7965-112">Eklenen dosyanın benzersiz kimliği depolanacağı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7965-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7965-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7965-113">Return Value</span></span>  
 <span data-ttu-id="a7965-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7965-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7965-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7965-115">Requirements</span></span>  
 <span data-ttu-id="a7965-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a7965-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7965-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7965-117">See also</span></span>
- [<span data-ttu-id="a7965-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7965-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a7965-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7965-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a7965-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="a7965-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
