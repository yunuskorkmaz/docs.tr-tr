---
title: EmitAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d73c158fa9d7b5574e4f875b8d51e932e30041b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572246"
---
# <a name="emitassembly-method"></a><span data-ttu-id="af95e-102">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af95e-102">EmitAssembly Method</span></span>
<span data-ttu-id="af95e-103">Bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af95e-103">Creates the assembly.</span></span> <span data-ttu-id="af95e-104">Bütünleştirilmiş kod dosyası dışında diğer tüm dosyalar kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="af95e-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="af95e-105">Bu yöntem, ilişkisiz modülleri üretirken çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="af95e-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af95e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af95e-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af95e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af95e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="af95e-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="af95e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af95e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="af95e-109">Return Value</span></span>  
 <span data-ttu-id="af95e-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="af95e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af95e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af95e-111">Requirements</span></span>  
 <span data-ttu-id="af95e-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="af95e-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af95e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af95e-113">See also</span></span>
- [<span data-ttu-id="af95e-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af95e-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="af95e-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af95e-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="af95e-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="af95e-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
