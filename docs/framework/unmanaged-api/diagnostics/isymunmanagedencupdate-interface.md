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
ms.openlocfilehash: 5e3c2ecd1bdd5c1181223c7500eb7473e20fa5d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731351"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="3028b-102">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3028b-102">ISymUnmanagedENCUpdate Interface</span></span>

<span data-ttu-id="3028b-103">Düzenle ve devam et özelliği için işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3028b-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3028b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3028b-104">Methods</span></span>  
  
|<span data-ttu-id="3028b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3028b-105">Method</span></span>|<span data-ttu-id="3028b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3028b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3028b-107">GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3028b-107">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="3028b-108">Yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3028b-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="3028b-109">GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3028b-109">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="3028b-110">Yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="3028b-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="3028b-111">InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3028b-111">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="3028b-112">Yöntem sınırlarının [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) metoduna ilk çağrıdan önce hesaplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3028b-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="3028b-113">UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3028b-113">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="3028b-114">Yeniden derlenmedi ancak satırları bağımsız olarak taşınmış olan bir yöntem için satır bilgilerinin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3028b-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="3028b-115">Her ifadeye yönelik bir Delta kullanımına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3028b-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="3028b-116">UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3028b-116">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="3028b-117">Bir derleyicinin, satır bilgilerinin gereksinimleri karşılaması şartıyla, program veritabanı (PDB) akışından değiştirilmeyen işlevleri yok saymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3028b-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="3028b-118">Doğru satır bilgileri, işlevdeki tüm satırlar için eski PDB satırı bilgileri ve bir Delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3028b-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3028b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3028b-119">Requirements</span></span>  

 <span data-ttu-id="3028b-120">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3028b-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3028b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3028b-121">See also</span></span>

- [<span data-ttu-id="3028b-122">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3028b-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
