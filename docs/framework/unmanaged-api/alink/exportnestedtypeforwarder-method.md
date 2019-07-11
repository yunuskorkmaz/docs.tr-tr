---
title: ExportNestedTypeForwarder Metodu
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb8fba433c5f7ef9701caf61971841672f46b425
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742031"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="c0582-102">ExportNestedTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="c0582-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="c0582-103">Bir iç içe geçmiş bir tür ileticisi verilen derleme türü tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="c0582-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0582-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0582-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0582-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0582-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c0582-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="c0582-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c0582-107">Belirteç veya derleme kimliği türü tanımlayan dosyasının dosya.</span><span class="sxs-lookup"><span data-stu-id="c0582-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="c0582-108">Belirteç türü.</span><span class="sxs-lookup"><span data-stu-id="c0582-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="c0582-109">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="c0582-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="c0582-110">Dışarı aktarmak için tam nitelikli tür adı.</span><span class="sxs-lookup"><span data-stu-id="c0582-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c0582-111">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="c0582-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="c0582-112">Dışarı aktarma türü belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="c0582-112">Receives token of export type.</span></span> <span data-ttu-id="c0582-113">Bu, iç içe geçmiş türler yalnızca yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c0582-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0582-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0582-114">Return Value</span></span>  
 <span data-ttu-id="c0582-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0582-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0582-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0582-116">Requirements</span></span>  
 <span data-ttu-id="c0582-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="c0582-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0582-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0582-118">See also</span></span>

- [<span data-ttu-id="c0582-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0582-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c0582-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0582-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c0582-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="c0582-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
