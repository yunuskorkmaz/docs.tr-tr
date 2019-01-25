---
title: ISymENCUnmanagedMethod Arabirimi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f46aeed0a303278fd67265e471bfa13b43cede12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680206"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="7fd50-102">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7fd50-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="7fd50-103">Düzenle ve devam et özelliği için bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fd50-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fd50-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7fd50-104">Methods</span></span>  
  
|<span data-ttu-id="7fd50-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7fd50-105">Method</span></span>|<span data-ttu-id="7fd50-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fd50-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fd50-107">GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fd50-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="7fd50-108">Bu yöntem satır var, belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="7fd50-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="7fd50-109">GetDocumentsForMethodCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fd50-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="7fd50-110">Bu yöntem satır var, belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7fd50-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="7fd50-111">GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fd50-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="7fd50-112">Bir uzaklık ile ilişkili satırı dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="7fd50-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="7fd50-113">GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fd50-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="7fd50-114">Bir uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="7fd50-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="7fd50-115">GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fd50-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="7fd50-116">Alır, özel bir belgede satır, metodu için satır sonu en büyük en küçük başlayın.</span><span class="sxs-lookup"><span data-stu-id="7fd50-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fd50-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7fd50-117">Requirements</span></span>  
 <span data-ttu-id="7fd50-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7fd50-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd50-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fd50-119">See also</span></span>
- [<span data-ttu-id="7fd50-120">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7fd50-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
