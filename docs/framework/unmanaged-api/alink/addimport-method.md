---
description: 'Daha fazla bilgi edinin: AddImport yöntemi'
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
ms.openlocfilehash: 9dca26501e66313b0932caf1288db7c909154e1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638606"
---
# <a name="addimport-method"></a><span data-ttu-id="5567c-103">AddImport Metodu</span><span class="sxs-lookup"><span data-stu-id="5567c-103">AddImport Method</span></span>

<span data-ttu-id="5567c-104">Derlemeye içeri aktarmalar ekler.</span><span class="sxs-lookup"><span data-stu-id="5567c-104">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5567c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5567c-105">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5567c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5567c-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="5567c-107">Artırılması için derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5567c-107">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="5567c-108">İçeri aktarılacak dosyanın [ImportFile yönteminden](importfile-method.md)ALıNAN benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="5567c-108">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5567c-109">Ve gibi COM+ FileDef bayrakları `ffContainsNoMetaData` `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="5567c-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="5567c-110">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5567c-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="5567c-111">Elde edilen dosyanın KIMLIĞINI alan belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5567c-111">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5567c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5567c-112">Return Value</span></span>  

 <span data-ttu-id="5567c-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="5567c-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5567c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5567c-114">Requirements</span></span>  

 <span data-ttu-id="5567c-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="5567c-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5567c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5567c-116">See also</span></span>

- [<span data-ttu-id="5567c-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5567c-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5567c-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5567c-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5567c-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="5567c-119">ALink API</span></span>](index.md)
