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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1406c68f1f6abff4d140b131f5f630d0fd767e1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787693"
---
# <a name="addfile-method"></a><span data-ttu-id="b86fd-102">AddFile Metodu</span><span class="sxs-lookup"><span data-stu-id="b86fd-102">AddFile Method</span></span>
<span data-ttu-id="b86fd-103">Derlemeye dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="b86fd-103">Adds files to the assembly.</span></span> <span data-ttu-id="b86fd-104">, İlişkisiz modüller oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b86fd-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b86fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b86fd-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b86fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b86fd-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b86fd-107">Artırılması için derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b86fd-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="b86fd-108">Eklenecek dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="b86fd-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b86fd-109">`ffContainsNoMetaData` Ve`ffWriteable`gibi com+ FileDef bayrakları.</span><span class="sxs-lookup"><span data-stu-id="b86fd-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="b86fd-110">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b86fd-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="b86fd-111">Gerekirse meta verileri yayan için kullanılacak [ımetadatayayma arabirimi](../metadata/imetadataemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b86fd-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="b86fd-112">Eklenen dosyanın benzersiz KIMLIĞININ depolanacağı işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b86fd-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b86fd-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b86fd-113">Return Value</span></span>  
 <span data-ttu-id="b86fd-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b86fd-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b86fd-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b86fd-115">Requirements</span></span>  
 <span data-ttu-id="b86fd-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b86fd-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b86fd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b86fd-117">See also</span></span>

- [<span data-ttu-id="b86fd-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b86fd-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b86fd-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b86fd-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b86fd-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="b86fd-120">ALink API</span></span>](index.md)
