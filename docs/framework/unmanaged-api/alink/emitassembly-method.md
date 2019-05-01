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
ms.openlocfilehash: bf7b54ab7a2318e8194bf39dbe41b864633ddb43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790071"
---
# <a name="emitassembly-method"></a><span data-ttu-id="3e603-102">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e603-102">EmitAssembly Method</span></span>
<span data-ttu-id="3e603-103">Bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e603-103">Creates the assembly.</span></span> <span data-ttu-id="3e603-104">Bütünleştirilmiş kod dosyası dışında diğer tüm dosyalar kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="3e603-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="3e603-105">Bu yöntem, ilişkisiz modülleri üretirken çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="3e603-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e603-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e603-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e603-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e603-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3e603-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="3e603-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e603-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3e603-109">Return Value</span></span>  
 <span data-ttu-id="3e603-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e603-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e603-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e603-111">Requirements</span></span>  
 <span data-ttu-id="3e603-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="3e603-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e603-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e603-113">See also</span></span>

- [<span data-ttu-id="3e603-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e603-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3e603-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e603-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3e603-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="3e603-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
