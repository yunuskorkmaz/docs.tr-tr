---
title: ISymUnmanagedENCUpdate Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f68d000824779fcffb90ec031b86b50e8c80eccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="3cfac-102">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cfac-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="3cfac-103">Düzenle ve devam et özelliği işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cfac-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3cfac-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3cfac-104">Methods</span></span>  
  
|<span data-ttu-id="3cfac-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3cfac-105">Method</span></span>|<span data-ttu-id="3cfac-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cfac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3cfac-107">GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cfac-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="3cfac-108">Yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3cfac-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="3cfac-109">GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cfac-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="3cfac-110">Yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="3cfac-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="3cfac-111">InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cfac-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="3cfac-112">Önce ilk çağrıda hesaplanacak yöntemi sınırları verir [Isymunmanagedencupdate::updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3cfac-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="3cfac-113">UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cfac-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="3cfac-114">Değil derlendikten ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgilerin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cfac-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="3cfac-115">Her deyim için bir delta izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3cfac-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="3cfac-116">UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cfac-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="3cfac-117">Program veritabanı (PDB) akışından değiştirilmiş işlevleri satır bilgilerini gereksinimlerini karşılayan koşuluyla atlamak bir derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cfac-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="3cfac-118">Doğru satır bilgilerini eski PDB satırı bilgileri ve işlev tüm satırlar için bir delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3cfac-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3cfac-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cfac-119">Requirements</span></span>  
 <span data-ttu-id="3cfac-120">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3cfac-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cfac-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3cfac-121">See Also</span></span>  
 [<span data-ttu-id="3cfac-122">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3cfac-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
