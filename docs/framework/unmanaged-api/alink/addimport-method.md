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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148674"
---
# <a name="addimport-method"></a><span data-ttu-id="c3377-102">AddImport Metodu</span><span class="sxs-lookup"><span data-stu-id="c3377-102">AddImport Method</span></span>
<span data-ttu-id="c3377-103">İçeri aktarmalar derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="c3377-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3377-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3377-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3377-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3377-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c3377-106">Derleme genişletilmesi benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3377-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="c3377-107">Öğesinden alınan benzersiz kimliği [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), içeri aktarılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="c3377-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c3377-108">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="c3377-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> `dwFlags` <span data-ttu-id="c3377-109">geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3377-109">is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c3377-110">Sonuç dosyası kimliği aldığı belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c3377-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3377-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3377-111">Return Value</span></span>  
 <span data-ttu-id="c3377-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3377-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3377-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3377-113">Requirements</span></span>  
 <span data-ttu-id="c3377-114">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="c3377-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3377-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3377-115">See also</span></span>

- [<span data-ttu-id="c3377-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3377-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c3377-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3377-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c3377-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="c3377-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
