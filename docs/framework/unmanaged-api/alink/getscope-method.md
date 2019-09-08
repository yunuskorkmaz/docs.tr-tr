---
title: GetScope Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a0e42e9ffb99896bdd09dbbab65eafb40cafff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777215"
---
# <a name="getscope-method"></a><span data-ttu-id="97c5a-102">GetScope Metodu</span><span class="sxs-lookup"><span data-stu-id="97c5a-102">GetScope Method</span></span>
<span data-ttu-id="97c5a-103">İçeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="97c5a-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c5a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97c5a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="97c5a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97c5a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="97c5a-106">İçeri aktarılacak derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="97c5a-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="97c5a-107">İçeri aktarılacak dosyanın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="97c5a-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="97c5a-108">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="97c5a-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="97c5a-109">Kapsam için [IMetaDataImport arabirimi](../metadata/imetadataimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="97c5a-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97c5a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97c5a-110">Return Value</span></span>  
 <span data-ttu-id="97c5a-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="97c5a-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97c5a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97c5a-112">Requirements</span></span>  
 <span data-ttu-id="97c5a-113">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="97c5a-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c5a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97c5a-114">See also</span></span>

- [<span data-ttu-id="97c5a-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97c5a-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="97c5a-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97c5a-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="97c5a-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="97c5a-117">ALink API</span></span>](index.md)
