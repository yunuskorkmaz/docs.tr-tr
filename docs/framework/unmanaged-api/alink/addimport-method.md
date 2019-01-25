---
title: Addımport Method1
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
ms.openlocfilehash: d2daed0450e04137621788e830bbedb467bd57c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706345"
---
# <a name="addimport-method1"></a><span data-ttu-id="70d27-102">Addımport Method1</span><span class="sxs-lookup"><span data-stu-id="70d27-102">AddImport Method1</span></span>
<span data-ttu-id="70d27-103">İçeri aktarmalar derlemesine ekler.</span><span class="sxs-lookup"><span data-stu-id="70d27-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70d27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70d27-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70d27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70d27-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="70d27-106">Derleme genişletilmesi benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="70d27-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="70d27-107">Öğesinden alınan benzersiz kimliği [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), içeri aktarılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="70d27-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="70d27-108">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="70d27-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="70d27-109">`dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="70d27-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="70d27-110">Sonuç dosyası kimliği aldığı belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="70d27-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70d27-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="70d27-111">Return Value</span></span>  
 <span data-ttu-id="70d27-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="70d27-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70d27-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70d27-113">Requirements</span></span>  
 <span data-ttu-id="70d27-114">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="70d27-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d27-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70d27-115">See also</span></span>
- [<span data-ttu-id="70d27-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70d27-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="70d27-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70d27-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="70d27-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="70d27-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
