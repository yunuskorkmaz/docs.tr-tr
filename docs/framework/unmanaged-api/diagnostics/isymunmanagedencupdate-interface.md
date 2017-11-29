---
title: ISymUnmanagedENCUpdate Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate
helpviewer_keywords: ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 36ac53094751cb43ef122d439c7a784070c28182
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="5fe2e-102">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fe2e-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="5fe2e-103">Düzenle ve devam et özelliği işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fe2e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5fe2e-104">Methods</span></span>  
  
|<span data-ttu-id="5fe2e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5fe2e-105">Method</span></span>|<span data-ttu-id="5fe2e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe2e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fe2e-107">GetLocalVariableCount yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe2e-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="5fe2e-108">Yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="5fe2e-109">GetLocalVariables yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe2e-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="5fe2e-110">Yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="5fe2e-111">Initializeforenc yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe2e-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="5fe2e-112">Önce ilk çağrıda hesaplanacak yöntemi sınırları verir [Isymunmanagedencupdate::updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="5fe2e-113">UpdateMethodLines yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe2e-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="5fe2e-114">Değil derlendikten ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgilerin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="5fe2e-115">Her deyim için bir delta izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="5fe2e-116">UpdateSymbolStore2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe2e-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="5fe2e-117">Program veritabanı (PDB) akışından değiştirilmiş işlevleri satır bilgilerini gereksinimlerini karşılayan koşuluyla atlamak bir derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="5fe2e-118">Doğru satır bilgilerini eski PDB satırı bilgileri ve işlev tüm satırlar için bir delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fe2e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fe2e-119">Requirements</span></span>  
 <span data-ttu-id="5fe2e-120">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5fe2e-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe2e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe2e-121">See Also</span></span>  
 [<span data-ttu-id="5fe2e-122">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5fe2e-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
