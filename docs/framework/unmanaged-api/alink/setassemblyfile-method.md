---
description: 'Daha fazla bilgi edinin: SetAssemblyFile yöntemi'
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
ms.openlocfilehash: 943e0600b9781aeaf45cc26e39bd8a8b33a783c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662500"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="53108-103">SetAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53108-103">SetAssemblyFile Method</span></span>

<span data-ttu-id="53108-104">Oluşturulacak derlemenin adını atar.</span><span class="sxs-lookup"><span data-stu-id="53108-104">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="53108-105">İlişkisiz modüller üretilirken kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="53108-105">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53108-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53108-106">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="53108-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53108-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="53108-108">Bildirim dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="53108-108">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="53108-109">[Imetadatayayma arabirim](../metadata/imetadataemit-interface.md) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="53108-109">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="53108-110">[AssemblyFlags numaralandırmasında](../metadata/assemblyflags-enumeration.md)tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="53108-110">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="53108-111">Elde edilen derlemenin KIMLIĞI işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="53108-111">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53108-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="53108-112">Return Value</span></span>  

 <span data-ttu-id="53108-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="53108-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53108-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53108-114">Requirements</span></span>  

 <span data-ttu-id="53108-115">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="53108-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53108-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53108-116">See also</span></span>

- [<span data-ttu-id="53108-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53108-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="53108-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53108-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="53108-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="53108-119">ALink API</span></span>](index.md)
