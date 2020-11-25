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
ms.openlocfilehash: cf73ada36be66edb3fa267d61873ae9acb088a34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717051"
---
# <a name="addimport-method"></a><span data-ttu-id="13f45-102">AddImport Metodu</span><span class="sxs-lookup"><span data-stu-id="13f45-102">AddImport Method</span></span>

<span data-ttu-id="13f45-103">Derlemeye içeri aktarmalar ekler.</span><span class="sxs-lookup"><span data-stu-id="13f45-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f45-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13f45-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="13f45-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13f45-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="13f45-106">Artırılması için derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="13f45-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="13f45-107">İçeri aktarılacak dosyanın [ImportFile yönteminden](importfile-method.md)ALıNAN benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="13f45-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="13f45-108">Ve gibi COM+ FileDef bayrakları `ffContainsNoMetaData` `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="13f45-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="13f45-109">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="13f45-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="13f45-110">Elde edilen dosyanın KIMLIĞINI alan belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="13f45-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13f45-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13f45-111">Return Value</span></span>  

 <span data-ttu-id="13f45-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="13f45-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13f45-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13f45-113">Requirements</span></span>  

 <span data-ttu-id="13f45-114">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="13f45-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f45-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13f45-115">See also</span></span>

- [<span data-ttu-id="13f45-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13f45-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="13f45-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13f45-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="13f45-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="13f45-118">ALink API</span></span>](index.md)
