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
ms.openlocfilehash: 575c732cf1b1caf4700568a9d168463359d1ad7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425509"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="369da-102">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="369da-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="369da-103">Düzenle ve devam et özelliği için bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="369da-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="369da-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="369da-104">Methods</span></span>  
  
|<span data-ttu-id="369da-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="369da-105">Method</span></span>|<span data-ttu-id="369da-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="369da-107">GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="369da-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="369da-108">Bu yöntem satırları cinsinden olan belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="369da-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="369da-109">GetDocumentsForMethodCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="369da-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="369da-110">Bu yöntem satırları cinsinden olan belgeleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="369da-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="369da-111">GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="369da-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="369da-112">Bir uzaklık ile ilişkili satırı dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="369da-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="369da-113">GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="369da-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="369da-114">Bir uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="369da-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="369da-115">GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="369da-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="369da-116">Alır en küçük satırı ve en büyük satır sonu yöntemi için özel bir belgede başlatın.</span><span class="sxs-lookup"><span data-stu-id="369da-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="369da-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="369da-117">Requirements</span></span>  
 <span data-ttu-id="369da-118">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="369da-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369da-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="369da-119">See Also</span></span>  
 [<span data-ttu-id="369da-120">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="369da-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
