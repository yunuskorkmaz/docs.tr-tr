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
ms.openlocfilehash: 47477bb473df8b568844d07bea704df681c9b95d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448601"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="689f6-102">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="689f6-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="689f6-103">Düzenle ve devam et özelliği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="689f6-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="689f6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="689f6-104">Methods</span></span>  
  
|<span data-ttu-id="689f6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="689f6-105">Method</span></span>|<span data-ttu-id="689f6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="689f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="689f6-107">GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="689f6-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="689f6-108">Bu yöntemin içindeki satırları içeren belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="689f6-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="689f6-109">GetDocumentsForMethodCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="689f6-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="689f6-110">Bu yöntemin içinde satır bulunan belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="689f6-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="689f6-111">GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="689f6-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="689f6-112">Bir uzaklığa ilişkin dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="689f6-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="689f6-113">GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="689f6-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="689f6-114">Bir uzaklığa ilişkin satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="689f6-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="689f6-115">GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="689f6-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="689f6-116">Belirli bir belgedeki Yöntem için en küçük başlangıç satırını ve en büyük bitiş satırını alır.</span><span class="sxs-lookup"><span data-stu-id="689f6-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="689f6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="689f6-117">Requirements</span></span>  
 <span data-ttu-id="689f6-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="689f6-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="689f6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="689f6-119">See also</span></span>

- [<span data-ttu-id="689f6-120">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="689f6-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
