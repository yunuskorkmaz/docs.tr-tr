---
title: ISymUnmanagedReader2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2
helpviewer_keywords: ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b23e166249659b94d454070c01c003495d1018a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="dfce3-102">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfce3-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="dfce3-103">Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfce3-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="dfce3-104">Bu arabirim genişletir [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dfce3-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dfce3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dfce3-105">Methods</span></span>  
  
|<span data-ttu-id="dfce3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dfce3-106">Method</span></span>|<span data-ttu-id="dfce3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfce3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfce3-108">GetMethodByVersionPreRemap yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfce3-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="dfce3-109">Verilen bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası alma simgesi okuyucu yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dfce3-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="dfce3-110">Getmethodsındocument yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfce3-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="dfce3-111">Sağlanan belgede satırı bilgileri içeren her yöntem alır.</span><span class="sxs-lookup"><span data-stu-id="dfce3-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="dfce3-112">GetSymAttributePreRemap yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfce3-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="dfce3-113">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="dfce3-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfce3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfce3-114">Requirements</span></span>  
 <span data-ttu-id="dfce3-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dfce3-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfce3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dfce3-116">See Also</span></span>  
 [<span data-ttu-id="dfce3-117">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dfce3-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="dfce3-118">Isymunmanagedreader arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfce3-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
