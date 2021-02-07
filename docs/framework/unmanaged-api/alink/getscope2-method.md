---
description: 'Daha fazla bilgi edinin: GetScope2 yöntemi'
title: GetScope2 Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 9a68f02a638b58e7a70207d8610607bf24b2b96b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718349"
---
# <a name="getscope2-method"></a><span data-ttu-id="9e186-103">GetScope2 Metodu</span><span class="sxs-lookup"><span data-stu-id="9e186-103">GetScope2 Method</span></span>

<span data-ttu-id="9e186-104">İçeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="9e186-104">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e186-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e186-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="9e186-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e186-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="9e186-107">Hedef derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9e186-107">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9e186-108">İçinden içeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9e186-108">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="9e186-109">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="9e186-109">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="9e186-110">Belirtilen kapsam için [IMetaDataImport2 arabirimi](../metadata/imetadataimport2-interface.md) arabirimine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9e186-110">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e186-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e186-111">Return Value</span></span>  

 <span data-ttu-id="9e186-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e186-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e186-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e186-113">Requirements</span></span>  

 <span data-ttu-id="9e186-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9e186-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e186-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e186-115">See also</span></span>

- [<span data-ttu-id="9e186-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e186-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9e186-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e186-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9e186-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="9e186-118">ALink API</span></span>](index.md)
