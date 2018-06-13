---
title: ISymUnmanagedENCUpdate Arabirimi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05cbe098b73dd817546dd72f0fc98ad548f75386
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425424"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="a1c18-102">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1c18-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="a1c18-103">Düzenle ve devam et özelliği işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1c18-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1c18-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a1c18-104">Methods</span></span>  
  
|<span data-ttu-id="a1c18-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a1c18-105">Method</span></span>|<span data-ttu-id="a1c18-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1c18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1c18-107">GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1c18-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="a1c18-108">Yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a1c18-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="a1c18-109">GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1c18-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="a1c18-110">Yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="a1c18-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="a1c18-111">InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1c18-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="a1c18-112">Önce ilk çağrıda hesaplanacak yöntemi sınırları verir [Isymunmanagedencupdate::updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a1c18-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="a1c18-113">UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1c18-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="a1c18-114">Değil derlendikten ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgilerin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1c18-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="a1c18-115">Her deyim için bir delta izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a1c18-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="a1c18-116">UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1c18-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="a1c18-117">Program veritabanı (PDB) akışından değiştirilmiş işlevleri satır bilgilerini gereksinimlerini karşılayan koşuluyla atlamak bir derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1c18-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="a1c18-118">Doğru satır bilgilerini eski PDB satırı bilgileri ve işlev tüm satırlar için bir delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a1c18-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1c18-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1c18-119">Requirements</span></span>  
 <span data-ttu-id="a1c18-120">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a1c18-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c18-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1c18-121">See Also</span></span>  
 [<span data-ttu-id="a1c18-122">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a1c18-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
