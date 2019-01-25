---
title: ISymUnmanagedReader2 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08695c4e5df6aaa63bedecf68b741302e5ddd8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524954"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="cce2d-102">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cce2d-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="cce2d-103">Belgeler, yöntemler ve değişkenler bir sembol deposundaki erişim sağlayan bir sembol okuyucu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cce2d-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="cce2d-104">Bu arabirim genişletir [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cce2d-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cce2d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cce2d-105">Methods</span></span>  
  
|<span data-ttu-id="cce2d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cce2d-106">Method</span></span>|<span data-ttu-id="cce2d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cce2d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cce2d-108">GetMethodByVersionPreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cce2d-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="cce2d-109">Bir sembol okuyucu yöntemi verilen token metody ve bir Düzenle ve devam et sürüm numarasını alın.</span><span class="sxs-lookup"><span data-stu-id="cce2d-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="cce2d-110">GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cce2d-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="cce2d-111">Sağlanan belge içinde satır bilgileri her yöntemin alır.</span><span class="sxs-lookup"><span data-stu-id="cce2d-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="cce2d-112">GetSymAttributePreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cce2d-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="cce2d-113">Özel bir öznitelik adı üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="cce2d-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cce2d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cce2d-114">Requirements</span></span>  
 <span data-ttu-id="cce2d-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cce2d-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce2d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cce2d-116">See also</span></span>
- [<span data-ttu-id="cce2d-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cce2d-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="cce2d-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cce2d-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
