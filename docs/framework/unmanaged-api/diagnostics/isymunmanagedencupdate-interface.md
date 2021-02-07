---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedencupdate arabirimi'
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
ms.openlocfilehash: 4527dfbba840be00cf87a80cdcef3cbde6f275df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721430"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="d6496-103">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6496-103">ISymUnmanagedENCUpdate Interface</span></span>

<span data-ttu-id="d6496-104">Düzenle ve devam et özelliği için işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6496-104">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6496-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d6496-105">Methods</span></span>  
  
|<span data-ttu-id="d6496-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d6496-106">Method</span></span>|<span data-ttu-id="d6496-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6496-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6496-108">GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6496-108">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="d6496-109">Yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d6496-109">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="d6496-110">GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6496-110">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="d6496-111">Yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="d6496-111">Gets the local variables.</span></span>|  
|[<span data-ttu-id="d6496-112">InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6496-112">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="d6496-113">Yöntem sınırlarının [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) metoduna ilk çağrıdan önce hesaplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6496-113">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="d6496-114">UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6496-114">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="d6496-115">Yeniden derlenmedi ancak satırları bağımsız olarak taşınmış olan bir yöntem için satır bilgilerinin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6496-115">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="d6496-116">Her ifadeye yönelik bir Delta kullanımına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d6496-116">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="d6496-117">UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6496-117">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="d6496-118">Bir derleyicinin, satır bilgilerinin gereksinimleri karşılaması şartıyla, program veritabanı (PDB) akışından değiştirilmeyen işlevleri yok saymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6496-118">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="d6496-119">Doğru satır bilgileri, işlevdeki tüm satırlar için eski PDB satırı bilgileri ve bir Delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="d6496-119">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6496-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6496-120">Requirements</span></span>  

 <span data-ttu-id="d6496-121">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d6496-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6496-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6496-122">See also</span></span>

- [<span data-ttu-id="d6496-123">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6496-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
