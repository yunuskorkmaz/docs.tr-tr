---
title: AddImport Metodu
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
ms.openlocfilehash: bbe8a43f44d59249abc713c95fce31f1fb9a5993
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775641"
---
# <a name="addimport-method"></a><span data-ttu-id="95a1d-102">AddImport Metodu</span><span class="sxs-lookup"><span data-stu-id="95a1d-102">AddImport Method</span></span>
<span data-ttu-id="95a1d-103">İçeri aktarmalar derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="95a1d-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a1d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95a1d-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="95a1d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95a1d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="95a1d-106">Derleme genişletilmesi benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="95a1d-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="95a1d-107">Öğesinden alınan benzersiz kimliği [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), içeri aktarılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="95a1d-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="95a1d-108">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="95a1d-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="95a1d-109">`dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="95a1d-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="95a1d-110">Sonuç dosyası kimliği aldığı belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="95a1d-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95a1d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="95a1d-111">Return Value</span></span>  
 <span data-ttu-id="95a1d-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="95a1d-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a1d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95a1d-113">Requirements</span></span>  
 <span data-ttu-id="95a1d-114">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="95a1d-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a1d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a1d-115">See also</span></span>

- [<span data-ttu-id="95a1d-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95a1d-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="95a1d-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95a1d-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="95a1d-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="95a1d-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
