---
title: SetPEKind Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179384"
---
# <a name="setpekind-method"></a><span data-ttu-id="0feb1-102">SetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0feb1-102">SetPEKind Method</span></span>
<span data-ttu-id="0feb1-103">Makineye özgü veya makineye özgü taşınabilir çalıştırılabilir türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="0feb1-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0feb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0feb1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="0feb1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0feb1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0feb1-106">Derlemenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="0feb1-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0feb1-107">PE türünün ayarlanabilmek için dosya belirteci.</span><span class="sxs-lookup"><span data-stu-id="0feb1-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="0feb1-108">Bağlanmamış bir `AssemblyID` ağ modül belirtmezise NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="0feb1-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="0feb1-109">[CorPEKind Numaralandırma](../metadata/corpekind-enumeration.md)da belirtildiği gibi PE türü.</span><span class="sxs-lookup"><span data-stu-id="0feb1-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="0feb1-110">Hedef makine mimarisi, NT üstbilgisinde belirtildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="0feb1-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0feb1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0feb1-111">Return Value</span></span>  
 <span data-ttu-id="0feb1-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0feb1-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0feb1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0feb1-113">Requirements</span></span>  
 <span data-ttu-id="0feb1-114">Alink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0feb1-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0feb1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0feb1-115">See also</span></span>

- [<span data-ttu-id="0feb1-116">GetPEKind Metodu</span><span class="sxs-lookup"><span data-stu-id="0feb1-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="0feb1-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0feb1-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0feb1-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0feb1-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0feb1-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="0feb1-119">ALink API</span></span>](index.md)
