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
ms.openlocfilehash: 1db4c4ab7e47e223a492e08297ac3cedcb3a27eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445596"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="be353-102">SetAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be353-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="be353-103">Oluşturulacak derlemenin adını atar.</span><span class="sxs-lookup"><span data-stu-id="be353-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="be353-104">İlişkisiz modüller üretilirken kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="be353-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be353-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be353-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="be353-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be353-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="be353-107">Bildirim dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="be353-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="be353-108">[Imetadatayayma arabirim](../metadata/imetadataemit-interface.md) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be353-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="be353-109">[AssemblyFlags numaralandırmasında](../metadata/assemblyflags-enumeration.md)tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="be353-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="be353-110">Elde edilen derlemenin KIMLIĞI işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="be353-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be353-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be353-111">Return Value</span></span>  
 <span data-ttu-id="be353-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="be353-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be353-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be353-113">Requirements</span></span>  
 <span data-ttu-id="be353-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="be353-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be353-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be353-115">See also</span></span>

- [<span data-ttu-id="be353-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be353-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="be353-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be353-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="be353-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="be353-118">ALink API</span></span>](index.md)
