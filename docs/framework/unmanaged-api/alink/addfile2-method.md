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
ms.openlocfilehash: cff6707496c7d9657796deb8bf6fa9165ff295a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717090"
---
# <a name="addfile2-method"></a><span data-ttu-id="51f4e-102">AddFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51f4e-102">AddFile2 Method</span></span>

<span data-ttu-id="51f4e-103">Derlemeye dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="51f4e-103">Adds files to the assembly.</span></span> <span data-ttu-id="51f4e-104">, İlişkisiz modüller oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51f4e-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51f4e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="51f4e-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="51f4e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51f4e-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="51f4e-107">Dosyanın eklendiği derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="51f4e-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="51f4e-108">Eklenecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="51f4e-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="51f4e-109">Ve gibi COM+ `FileDef` bayrakları `ffContainsNoMetaData` `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="51f4e-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="51f4e-110">`dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.</span><span class="sxs-lookup"><span data-stu-id="51f4e-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="51f4e-111">Arabirim arabirimine [IMetaDataEmit2](../metadata/imetadataemit2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="51f4e-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="51f4e-112">Eklenmekte olan dosyanın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="51f4e-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51f4e-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="51f4e-113">Return Value</span></span>  

 <span data-ttu-id="51f4e-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="51f4e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51f4e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51f4e-115">Requirements</span></span>  

 <span data-ttu-id="51f4e-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="51f4e-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f4e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51f4e-117">See also</span></span>

- [<span data-ttu-id="51f4e-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51f4e-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="51f4e-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51f4e-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="51f4e-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="51f4e-120">ALink API</span></span>](index.md)
