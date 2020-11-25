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
ms.openlocfilehash: acb8d48ed6314756e2c1a10fff314a303799fb24
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707288"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="6744d-102">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6744d-102">ISymENCUnmanagedMethod Interface</span></span>

<span data-ttu-id="6744d-103">Düzenle ve devam et özelliği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6744d-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6744d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6744d-104">Methods</span></span>  
  
|<span data-ttu-id="6744d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6744d-105">Method</span></span>|<span data-ttu-id="6744d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6744d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6744d-107">GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6744d-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="6744d-108">Bu yöntemin içindeki satırları içeren belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="6744d-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="6744d-109">GetDocumentsForMethodCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6744d-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="6744d-110">Bu yöntemin içinde satır bulunan belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6744d-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="6744d-111">GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6744d-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="6744d-112">Bir uzaklığa ilişkin dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="6744d-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="6744d-113">GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6744d-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="6744d-114">Bir uzaklığa ilişkin satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6744d-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="6744d-115">GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6744d-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="6744d-116">Belirli bir belgedeki Yöntem için en küçük başlangıç satırını ve en büyük bitiş satırını alır.</span><span class="sxs-lookup"><span data-stu-id="6744d-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6744d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6744d-117">Requirements</span></span>  

 <span data-ttu-id="6744d-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6744d-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6744d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6744d-119">See also</span></span>

- [<span data-ttu-id="6744d-120">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6744d-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
