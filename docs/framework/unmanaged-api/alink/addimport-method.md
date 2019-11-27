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
ms.openlocfilehash: 52e52ac62e2dcfeb182da3014a863409f640274e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446659"
---
# <a name="addimport-method"></a><span data-ttu-id="64b52-102">AddImport Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64b52-102">AddImport Method</span></span>
<span data-ttu-id="64b52-103">Derlemeye içeri aktarmalar ekler.</span><span class="sxs-lookup"><span data-stu-id="64b52-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64b52-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="64b52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64b52-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="64b52-106">Artırılması için derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="64b52-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="64b52-107">İçeri aktarılacak dosyanın [ImportFile yönteminden](importfile-method.md)ALıNAN benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="64b52-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="64b52-108">`ffContainsNoMetaData` ve `ffWriteable`gibi COM+ Fıledef bayrakları.</span><span class="sxs-lookup"><span data-stu-id="64b52-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="64b52-109">`dwFlags` [DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="64b52-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="64b52-110">Elde edilen dosyanın KIMLIĞINI alan belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="64b52-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64b52-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64b52-111">Return Value</span></span>  
 <span data-ttu-id="64b52-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="64b52-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64b52-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64b52-113">Requirements</span></span>  
 <span data-ttu-id="64b52-114">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="64b52-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b52-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64b52-115">See also</span></span>

- [<span data-ttu-id="64b52-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64b52-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="64b52-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64b52-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="64b52-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="64b52-118">ALink API</span></span>](index.md)
