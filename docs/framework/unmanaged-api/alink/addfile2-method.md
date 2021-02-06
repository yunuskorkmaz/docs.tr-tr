---
description: 'Daha fazla bilgi edinin: AddFile2 yöntemi'
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
ms.openlocfilehash: d53527ecf7e8b3a99a11ea99512fbc812125de3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638619"
---
# <a name="addfile2-method"></a><span data-ttu-id="25a92-103">AddFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25a92-103">AddFile2 Method</span></span>

<span data-ttu-id="25a92-104">Derlemeye dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="25a92-104">Adds files to the assembly.</span></span> <span data-ttu-id="25a92-105">, İlişkisiz modüller oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25a92-105">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a92-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25a92-106">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="25a92-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25a92-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="25a92-108">Dosyanın eklendiği derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="25a92-108">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="25a92-109">Eklenecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="25a92-109">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="25a92-110">Ve gibi COM+ `FileDef` bayrakları `ffContainsNoMetaData` `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="25a92-110">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="25a92-111">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="25a92-111">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="25a92-112">Arabirim arabirimine [IMetaDataEmit2](../metadata/imetadataemit2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="25a92-112">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="25a92-113">Eklenmekte olan dosyanın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="25a92-113">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25a92-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25a92-114">Return Value</span></span>  

 <span data-ttu-id="25a92-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="25a92-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25a92-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25a92-116">Requirements</span></span>  

 <span data-ttu-id="25a92-117">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="25a92-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a92-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25a92-118">See also</span></span>

- [<span data-ttu-id="25a92-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25a92-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="25a92-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25a92-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="25a92-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="25a92-121">ALink API</span></span>](index.md)
