---
title: ISymENCUnmanagedMethod Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod
helpviewer_keywords: ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7cc1cea74cc632c65c7e3c2aee408e2f9e864d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="0a284-102">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a284-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="0a284-103">Düzenle ve devam et özelliği için bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a284-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a284-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0a284-104">Methods</span></span>  
  
|<span data-ttu-id="0a284-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0a284-105">Method</span></span>|<span data-ttu-id="0a284-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a284-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a284-107">GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a284-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="0a284-108">Bu yöntem satırları cinsinden olan belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="0a284-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="0a284-109">GetDocumentsForMethodCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a284-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="0a284-110">Bu yöntem satırları cinsinden olan belgeleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0a284-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="0a284-111">GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a284-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="0a284-112">Bir uzaklık ile ilişkili satırı dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="0a284-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="0a284-113">GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a284-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="0a284-114">Bir uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="0a284-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="0a284-115">GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a284-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="0a284-116">Alır en küçük satırı ve en büyük satır sonu yöntemi için özel bir belgede başlatın.</span><span class="sxs-lookup"><span data-stu-id="0a284-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a284-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a284-117">Requirements</span></span>  
 <span data-ttu-id="0a284-118">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0a284-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a284-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a284-119">See Also</span></span>  
 [<span data-ttu-id="0a284-120">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a284-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
