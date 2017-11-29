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
ms.openlocfilehash: 68929dc30b029133c73f18c3749f39f014359c0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="e67d7-102">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e67d7-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="e67d7-103">Düzenle ve devam et özelliği için bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e67d7-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e67d7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e67d7-104">Methods</span></span>  
  
|<span data-ttu-id="e67d7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e67d7-105">Method</span></span>|<span data-ttu-id="e67d7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e67d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e67d7-107">GetDocumentsForMethod yöntemi</span><span class="sxs-lookup"><span data-stu-id="e67d7-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="e67d7-108">Bu yöntem satırları cinsinden olan belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="e67d7-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e67d7-109">GetDocumentsForMethodCount yöntemi</span><span class="sxs-lookup"><span data-stu-id="e67d7-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="e67d7-110">Bu yöntem satırları cinsinden olan belgeleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e67d7-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e67d7-111">GetFileNameFromOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="e67d7-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="e67d7-112">Bir uzaklık ile ilişkili satırı dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="e67d7-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="e67d7-113">GetLineFromOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="e67d7-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="e67d7-114">Bir uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e67d7-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="e67d7-115">Getsourceextentındocument yöntemi</span><span class="sxs-lookup"><span data-stu-id="e67d7-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="e67d7-116">Alır en küçük satırı ve en büyük satır sonu yöntemi için özel bir belgede başlatın.</span><span class="sxs-lookup"><span data-stu-id="e67d7-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e67d7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e67d7-117">Requirements</span></span>  
 <span data-ttu-id="e67d7-118">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e67d7-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67d7-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e67d7-119">See Also</span></span>  
 [<span data-ttu-id="e67d7-120">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e67d7-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
