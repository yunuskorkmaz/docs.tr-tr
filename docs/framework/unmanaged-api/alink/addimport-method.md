---
title: AddImport Yöntemi
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95a434cc365e12aa19d164951726ddad8945f60d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974139"
---
# <a name="addimport-method"></a><span data-ttu-id="1410a-102">AddImport Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1410a-102">AddImport Method</span></span>
<span data-ttu-id="1410a-103">İçeri aktarmalar derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="1410a-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1410a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1410a-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1410a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1410a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1410a-106">Derleme genişletilmesi benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="1410a-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="1410a-107">Öğesinden alınan benzersiz kimliği [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), içeri aktarılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="1410a-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1410a-108">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="1410a-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="1410a-109">`dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="1410a-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="1410a-110">Sonuç dosyası kimliği aldığı belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1410a-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1410a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1410a-111">Return Value</span></span>  
 <span data-ttu-id="1410a-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="1410a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1410a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1410a-113">Requirements</span></span>  
 <span data-ttu-id="1410a-114">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="1410a-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1410a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1410a-115">See also</span></span>
- [<span data-ttu-id="1410a-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1410a-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1410a-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1410a-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1410a-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="1410a-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
