---
title: SetAssemblyFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d341aca7c96e5932a1fc155ccaee17ce6585da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777006"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="11cef-102">SetAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11cef-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="11cef-103">Oluşturulacak derlemenin adını atar.</span><span class="sxs-lookup"><span data-stu-id="11cef-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="11cef-104">İlişkisiz modüller üretilirken kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="11cef-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11cef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11cef-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="11cef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11cef-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="11cef-107">Bildirim dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="11cef-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="11cef-108">[Imetadatayayma arabirim](../metadata/imetadataemit-interface.md) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="11cef-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="11cef-109">[AssemblyFlags numaralandırmasında](../metadata/assemblyflags-enumeration.md)tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="11cef-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="11cef-110">Elde edilen derlemenin KIMLIĞI işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="11cef-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11cef-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="11cef-111">Return Value</span></span>  
 <span data-ttu-id="11cef-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="11cef-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11cef-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11cef-113">Requirements</span></span>  
 <span data-ttu-id="11cef-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="11cef-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11cef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11cef-115">See also</span></span>

- [<span data-ttu-id="11cef-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11cef-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="11cef-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11cef-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="11cef-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="11cef-118">ALink API</span></span>](index.md)
