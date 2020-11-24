---
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
ms.openlocfilehash: 34439b7c01dee7d7789d989b58e8944c6282b71b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676393"
---
# <a name="embedresource-method"></a><span data-ttu-id="dda9b-102">EmbedResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dda9b-102">EmbedResource Method</span></span>

<span data-ttu-id="dda9b-103">Gömülü bir kaynak bildirir.</span><span class="sxs-lookup"><span data-stu-id="dda9b-103">Declares an embedded resource.</span></span> <span data-ttu-id="dda9b-104">Bu yöntem, kaynağı aslında eklemez.</span><span class="sxs-lookup"><span data-stu-id="dda9b-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda9b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dda9b-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="dda9b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dda9b-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="dda9b-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dda9b-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="dda9b-108">Kaynağı içeren dosyanın belirteç veya derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dda9b-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="dda9b-109">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="dda9b-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="dda9b-110">Kaynak RVA 'dan konum.</span><span class="sxs-lookup"><span data-stu-id="dda9b-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dda9b-111">Ve gibi erişilebilirlik bayrakları `mrPublic` `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="dda9b-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="dda9b-112">Bu bayraklar [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dda9b-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dda9b-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dda9b-113">Return Value</span></span>  

 <span data-ttu-id="dda9b-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="dda9b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda9b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dda9b-115">Requirements</span></span>  

 <span data-ttu-id="dda9b-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dda9b-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda9b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dda9b-117">See also</span></span>

- [<span data-ttu-id="dda9b-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dda9b-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="dda9b-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dda9b-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="dda9b-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="dda9b-120">ALink API</span></span>](index.md)
