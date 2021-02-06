---
description: 'Daha fazla bilgi edinin: EmbedResource yöntemi'
title: EmbedResource Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: f7896172e7416048352788caf7e092096924b7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638359"
---
# <a name="embedresource-method"></a><span data-ttu-id="460bf-103">EmbedResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="460bf-103">EmbedResource Method</span></span>

<span data-ttu-id="460bf-104">Gömülü bir kaynak bildirir.</span><span class="sxs-lookup"><span data-stu-id="460bf-104">Declares an embedded resource.</span></span> <span data-ttu-id="460bf-105">Bu yöntem, kaynağı aslında eklemez.</span><span class="sxs-lookup"><span data-stu-id="460bf-105">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="460bf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="460bf-106">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="460bf-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="460bf-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="460bf-108">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="460bf-108">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="460bf-109">Kaynağı içeren dosyanın belirteç veya derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="460bf-109">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="460bf-110">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="460bf-110">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="460bf-111">Kaynak RVA 'dan konum.</span><span class="sxs-lookup"><span data-stu-id="460bf-111">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="460bf-112">Ve gibi erişilebilirlik bayrakları `mrPublic` `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="460bf-112">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="460bf-113">Bu bayraklar [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="460bf-113">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="460bf-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="460bf-114">Return Value</span></span>  

 <span data-ttu-id="460bf-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="460bf-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="460bf-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="460bf-116">Requirements</span></span>  

 <span data-ttu-id="460bf-117">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="460bf-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="460bf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="460bf-118">See also</span></span>

- [<span data-ttu-id="460bf-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="460bf-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="460bf-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="460bf-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="460bf-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="460bf-121">ALink API</span></span>](index.md)
