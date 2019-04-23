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
ms.openlocfilehash: 378322c28d59b2a6e7c09f2f2c4bf55bb019d01d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171846"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="2293d-102">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2293d-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="2293d-103">İşlevler için Düzenle ve devam et özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2293d-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2293d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2293d-104">Methods</span></span>  
  
|<span data-ttu-id="2293d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2293d-105">Method</span></span>|<span data-ttu-id="2293d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2293d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2293d-107">GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2293d-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="2293d-108">Yerel değişken sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2293d-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="2293d-109">GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2293d-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="2293d-110">Yerel değişkenlerini alır.</span><span class="sxs-lookup"><span data-stu-id="2293d-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="2293d-111">InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2293d-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="2293d-112">İlk çağırmadan önce hesaplanmasını yöntemi sınırlarıyla sağlayan [Isymunmanagedencupdate::updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2293d-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="2293d-113">UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2293d-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="2293d-114">Değil derlendiği ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgileri güncelleniyor sağlar.</span><span class="sxs-lookup"><span data-stu-id="2293d-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="2293d-115">Her deyim için bir delta izin verilir.</span><span class="sxs-lookup"><span data-stu-id="2293d-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="2293d-116">UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2293d-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="2293d-117">Program veritabanı (PDB) akışından değiştirilmiş işlevleri satır bilgilerini gereksinimleri karşılaması koşuluyla atlamak bir derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="2293d-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="2293d-118">Doğru satır bilgilerini eski PDB satır bilgileri ve tüm satırları işlevi için bir delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="2293d-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2293d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2293d-119">Requirements</span></span>  
 <span data-ttu-id="2293d-120">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2293d-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2293d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2293d-121">See also</span></span>

- [<span data-ttu-id="2293d-122">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2293d-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
