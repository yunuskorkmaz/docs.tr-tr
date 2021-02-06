---
description: 'Daha fazla bilgi edinin: AddFile yöntemi'
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
ms.openlocfilehash: 5e1253587298b2c1559c72dced43ec70dc169090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638632"
---
# <a name="addfile-method"></a><span data-ttu-id="c94ab-103">AddFile Metodu</span><span class="sxs-lookup"><span data-stu-id="c94ab-103">AddFile Method</span></span>

<span data-ttu-id="c94ab-104">Derlemeye dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="c94ab-104">Adds files to the assembly.</span></span> <span data-ttu-id="c94ab-105">, İlişkisiz modüller oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c94ab-105">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94ab-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c94ab-106">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c94ab-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c94ab-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c94ab-108">Artırılması için derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c94ab-108">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="c94ab-109">Eklenecek dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="c94ab-109">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c94ab-110">Ve gibi COM+ FileDef bayrakları `ffContainsNoMetaData` `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="c94ab-110">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="c94ab-111">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c94ab-111">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c94ab-112">Gerekirse meta verileri yayan için kullanılacak [ımetadatayayma arabirimi](../metadata/imetadataemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c94ab-112">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c94ab-113">Eklenen dosyanın benzersiz KIMLIĞININ depolanacağı işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c94ab-113">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c94ab-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c94ab-114">Return Value</span></span>  

 <span data-ttu-id="c94ab-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c94ab-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94ab-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c94ab-116">Requirements</span></span>  

 <span data-ttu-id="c94ab-117">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c94ab-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94ab-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c94ab-118">See also</span></span>

- [<span data-ttu-id="c94ab-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c94ab-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c94ab-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c94ab-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c94ab-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="c94ab-121">ALink API</span></span>](index.md)
