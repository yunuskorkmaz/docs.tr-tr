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
ms.openlocfilehash: fd5ae6ef40cb171c33132df0f640acbef96d69b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684686"
---
# <a name="getscope-method"></a><span data-ttu-id="9bfc9-102">GetScope Metodu</span><span class="sxs-lookup"><span data-stu-id="9bfc9-102">GetScope Method</span></span>

<span data-ttu-id="9bfc9-103">İçeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="9bfc9-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bfc9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9bfc9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bfc9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bfc9-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="9bfc9-106">İçeri aktarılacak derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9bfc9-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9bfc9-107">İçeri aktarılacak dosyanın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9bfc9-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="9bfc9-108">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="9bfc9-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="9bfc9-109">Kapsam için [IMetaDataImport arabirimi](../metadata/imetadataimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="9bfc9-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bfc9-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9bfc9-110">Return Value</span></span>  

 <span data-ttu-id="9bfc9-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="9bfc9-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bfc9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bfc9-112">Requirements</span></span>  

 <span data-ttu-id="9bfc9-113">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="9bfc9-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfc9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bfc9-114">See also</span></span>

- [<span data-ttu-id="9bfc9-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bfc9-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9bfc9-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bfc9-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9bfc9-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="9bfc9-117">ALink API</span></span>](index.md)
