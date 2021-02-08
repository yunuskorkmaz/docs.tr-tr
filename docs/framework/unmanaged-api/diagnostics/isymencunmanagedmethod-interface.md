---
description: 'Şu konuda daha fazla bilgi edinin: ISymENCUnmanagedMethod arabirimi'
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
ms.openlocfilehash: 59dd56c20279b2507fc4432182d0abb5b3e9c289
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790327"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="e4d4f-103">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4d4f-103">ISymENCUnmanagedMethod Interface</span></span>

<span data-ttu-id="e4d4f-104">Düzenle ve devam et özelliği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4d4f-104">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4d4f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e4d4f-105">Methods</span></span>  
  
|<span data-ttu-id="e4d4f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e4d4f-106">Method</span></span>|<span data-ttu-id="e4d4f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4d4f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4d4f-108">GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4d4f-108">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="e4d4f-109">Bu yöntemin içindeki satırları içeren belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="e4d4f-109">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e4d4f-110">GetDocumentsForMethodCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4d4f-110">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="e4d4f-111">Bu yöntemin içinde satır bulunan belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e4d4f-111">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="e4d4f-112">GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4d4f-112">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="e4d4f-113">Bir uzaklığa ilişkin dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="e4d4f-113">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="e4d4f-114">GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4d4f-114">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="e4d4f-115">Bir uzaklığa ilişkin satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e4d4f-115">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="e4d4f-116">GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4d4f-116">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="e4d4f-117">Belirli bir belgedeki Yöntem için en küçük başlangıç satırını ve en büyük bitiş satırını alır.</span><span class="sxs-lookup"><span data-stu-id="e4d4f-117">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4d4f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4d4f-118">Requirements</span></span>  

 <span data-ttu-id="e4d4f-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e4d4f-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d4f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4d4f-120">See also</span></span>

- [<span data-ttu-id="e4d4f-121">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e4d4f-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
