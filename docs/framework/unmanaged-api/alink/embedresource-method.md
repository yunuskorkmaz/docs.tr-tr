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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f6140e5f85a7ee21773c96a5abdccadaddab92e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777451"
---
# <a name="embedresource-method"></a><span data-ttu-id="2dc5e-102">EmbedResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2dc5e-102">EmbedResource Method</span></span>
<span data-ttu-id="2dc5e-103">Gömülü bir kaynak bildirir.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-103">Declares an embedded resource.</span></span> <span data-ttu-id="2dc5e-104">Bu yöntem, kaynağı aslında eklemez.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc5e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2dc5e-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dc5e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2dc5e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2dc5e-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2dc5e-108">Kaynağı içeren dosyanın belirteç veya derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="2dc5e-109">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="2dc5e-110">Kaynak RVA 'dan konum.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2dc5e-111">`mrPublic` Ve`mrPrivate`gibi erişilebilirlik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="2dc5e-112">Bu bayraklar [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dc5e-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2dc5e-113">Return Value</span></span>  
 <span data-ttu-id="2dc5e-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dc5e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2dc5e-115">Requirements</span></span>  
 <span data-ttu-id="2dc5e-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc5e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dc5e-117">See also</span></span>

- [<span data-ttu-id="2dc5e-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2dc5e-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2dc5e-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2dc5e-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2dc5e-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="2dc5e-120">ALink API</span></span>](index.md)
