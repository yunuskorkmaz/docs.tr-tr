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
ms.openlocfilehash: 1986d5f91a3dcfa31a43f729ee1f50129e083f5f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501748"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="c75bb-102">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c75bb-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="c75bb-103">Düzenle ve devam et özelliği için işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c75bb-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c75bb-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c75bb-104">Methods</span></span>  
  
|<span data-ttu-id="c75bb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c75bb-105">Method</span></span>|<span data-ttu-id="c75bb-106">Description</span><span class="sxs-lookup"><span data-stu-id="c75bb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c75bb-107">GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75bb-107">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="c75bb-108">Yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c75bb-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="c75bb-109">GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75bb-109">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="c75bb-110">Yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="c75bb-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="c75bb-111">InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75bb-111">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="c75bb-112">Yöntem sınırlarının [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) metoduna ilk çağrıdan önce hesaplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c75bb-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="c75bb-113">UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75bb-113">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="c75bb-114">Yeniden derlenmedi ancak satırları bağımsız olarak taşınmış olan bir yöntem için satır bilgilerinin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c75bb-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="c75bb-115">Her ifadeye yönelik bir Delta kullanımına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c75bb-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="c75bb-116">UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75bb-116">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="c75bb-117">Bir derleyicinin, satır bilgilerinin gereksinimleri karşılaması şartıyla, program veritabanı (PDB) akışından değiştirilmeyen işlevleri yok saymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c75bb-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="c75bb-118">Doğru satır bilgileri, işlevdeki tüm satırlar için eski PDB satırı bilgileri ve bir Delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c75bb-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c75bb-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c75bb-119">Requirements</span></span>  
 <span data-ttu-id="c75bb-120">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c75bb-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75bb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c75bb-121">See also</span></span>

- [<span data-ttu-id="c75bb-122">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c75bb-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
