---
title: ExportTypeForwarder Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 36c99477e9faead5e24799d5b0ae8901f1dd13c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448715"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="88a7d-102">ExportTypeForwarder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88a7d-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="88a7d-103">Verilen derlemenin tür tablosuna bir tür ileticisi ekler.</span><span class="sxs-lookup"><span data-stu-id="88a7d-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88a7d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="88a7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88a7d-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="88a7d-106">Tür ileticinin başvurduğu derlemeye başvuru.</span><span class="sxs-lookup"><span data-stu-id="88a7d-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="88a7d-107">Dışarı aktarılacak tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="88a7d-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="88a7d-108">`tdPublic` veya `tdNested`gibi bayrakları `ComType`.</span><span class="sxs-lookup"><span data-stu-id="88a7d-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="88a7d-109">Bu değer [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="88a7d-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="88a7d-110">, Dışarıya aktarılmış türün belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="88a7d-110">Receives the token of the exported type.</span></span> <span data-ttu-id="88a7d-111">Bu yalnızca iç içe geçmiş türleri yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="88a7d-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88a7d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="88a7d-112">Return Value</span></span>  
 <span data-ttu-id="88a7d-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="88a7d-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a7d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88a7d-114">Requirements</span></span>  
 <span data-ttu-id="88a7d-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="88a7d-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a7d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88a7d-116">See also</span></span>

- [<span data-ttu-id="88a7d-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88a7d-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="88a7d-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88a7d-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="88a7d-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="88a7d-119">ALink API</span></span>](index.md)
