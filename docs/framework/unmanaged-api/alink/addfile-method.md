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
ms.openlocfilehash: 53ca4005f5681cfc5d550301d8aad1406aceb3a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717207"
---
# <a name="addfile-method"></a><span data-ttu-id="74d25-102">AddFile Metodu</span><span class="sxs-lookup"><span data-stu-id="74d25-102">AddFile Method</span></span>

<span data-ttu-id="74d25-103">Derlemeye dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="74d25-103">Adds files to the assembly.</span></span> <span data-ttu-id="74d25-104">, İlişkisiz modüller oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74d25-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d25-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="74d25-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="74d25-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74d25-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="74d25-107">Artırılması için derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="74d25-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="74d25-108">Eklenecek dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="74d25-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="74d25-109">Ve gibi COM+ FileDef bayrakları `ffContainsNoMetaData` `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="74d25-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="74d25-110">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="74d25-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="74d25-111">Gerekirse meta verileri yayan için kullanılacak [ımetadatayayma arabirimi](../metadata/imetadataemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="74d25-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="74d25-112">Eklenen dosyanın benzersiz KIMLIĞININ depolanacağı işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74d25-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74d25-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="74d25-113">Return Value</span></span>  

 <span data-ttu-id="74d25-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="74d25-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74d25-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74d25-115">Requirements</span></span>  

 <span data-ttu-id="74d25-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74d25-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d25-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74d25-117">See also</span></span>

- [<span data-ttu-id="74d25-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74d25-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="74d25-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74d25-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="74d25-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="74d25-120">ALink API</span></span>](index.md)
