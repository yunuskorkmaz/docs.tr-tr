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
ms.openlocfilehash: 24279870e7406de649df56e8aad31252513e95c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446543"
---
# <a name="embedresource-method"></a><span data-ttu-id="e5085-102">EmbedResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5085-102">EmbedResource Method</span></span>
<span data-ttu-id="e5085-103">Gömülü bir kaynak bildirir.</span><span class="sxs-lookup"><span data-stu-id="e5085-103">Declares an embedded resource.</span></span> <span data-ttu-id="e5085-104">Bu yöntem, kaynağı aslında eklemez.</span><span class="sxs-lookup"><span data-stu-id="e5085-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5085-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5085-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5085-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5085-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e5085-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e5085-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e5085-108">Kaynağı içeren dosyanın belirteç veya derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e5085-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="e5085-109">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="e5085-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="e5085-110">Kaynak RVA 'dan konum.</span><span class="sxs-lookup"><span data-stu-id="e5085-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e5085-111">`mrPublic` ve `mrPrivate`gibi erişilebilirlik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="e5085-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="e5085-112">Bu bayraklar [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e5085-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5085-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e5085-113">Return Value</span></span>  
 <span data-ttu-id="e5085-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5085-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5085-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5085-115">Requirements</span></span>  
 <span data-ttu-id="e5085-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5085-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5085-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5085-117">See also</span></span>

- [<span data-ttu-id="e5085-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5085-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e5085-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5085-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e5085-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="e5085-120">ALink API</span></span>](index.md)
