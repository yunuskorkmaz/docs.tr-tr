---
title: AddFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3a6892dbed172c0be3b036014d393657dbc8593
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777526"
---
# <a name="addfile2-method"></a><span data-ttu-id="54bc2-102">AddFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54bc2-102">AddFile2 Method</span></span>
<span data-ttu-id="54bc2-103">Derlemeye dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="54bc2-103">Adds files to the assembly.</span></span> <span data-ttu-id="54bc2-104">, İlişkisiz modüller oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54bc2-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54bc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54bc2-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="54bc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54bc2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="54bc2-107">Dosyanın eklendiği derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="54bc2-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="54bc2-108">Eklenecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="54bc2-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="54bc2-109">`ffContainsNoMetaData` `FileDef` Ve`ffWriteable`gibi com+ bayrakları.</span><span class="sxs-lookup"><span data-stu-id="54bc2-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="54bc2-110">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="54bc2-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="54bc2-111">Arabirim arabirimine [IMetaDataEmit2](../metadata/imetadataemit2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="54bc2-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="54bc2-112">Eklenmekte olan dosyanın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="54bc2-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54bc2-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="54bc2-113">Return Value</span></span>  
 <span data-ttu-id="54bc2-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="54bc2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54bc2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54bc2-115">Requirements</span></span>  
 <span data-ttu-id="54bc2-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="54bc2-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54bc2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54bc2-117">See also</span></span>

- [<span data-ttu-id="54bc2-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54bc2-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="54bc2-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54bc2-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="54bc2-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="54bc2-120">ALink API</span></span>](index.md)
