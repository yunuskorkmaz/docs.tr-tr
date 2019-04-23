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
ms.openlocfilehash: 4474269688094ea6c81b06659727acfb9c2ad6c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095717"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="775c0-102">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="775c0-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="775c0-103">Düzenle ve devam et özelliği için bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="775c0-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="775c0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="775c0-104">Methods</span></span>  
  
|<span data-ttu-id="775c0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="775c0-105">Method</span></span>|<span data-ttu-id="775c0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="775c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="775c0-107">GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="775c0-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="775c0-108">Bu yöntem satır var, belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="775c0-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="775c0-109">GetDocumentsForMethodCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="775c0-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="775c0-110">Bu yöntem satır var, belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="775c0-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="775c0-111">GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="775c0-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="775c0-112">Bir uzaklık ile ilişkili satırı dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="775c0-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="775c0-113">GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="775c0-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="775c0-114">Bir uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="775c0-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="775c0-115">GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="775c0-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="775c0-116">Alır, özel bir belgede satır, metodu için satır sonu en büyük en küçük başlayın.</span><span class="sxs-lookup"><span data-stu-id="775c0-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="775c0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="775c0-117">Requirements</span></span>  
 <span data-ttu-id="775c0-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="775c0-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775c0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="775c0-119">See also</span></span>

- [<span data-ttu-id="775c0-120">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="775c0-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
