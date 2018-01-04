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
ms.workload: dotnet
ms.openlocfilehash: 93f4b88d891d7b5c1d92006276a290841372aad7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="c6a37-102">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6a37-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="c6a37-103">Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6a37-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="c6a37-104">Bu arabirim genişletir [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c6a37-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6a37-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c6a37-105">Methods</span></span>  
  
|<span data-ttu-id="c6a37-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c6a37-106">Method</span></span>|<span data-ttu-id="c6a37-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6a37-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6a37-108">GetMethodByVersionPreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a37-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="c6a37-109">Verilen bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası alma simgesi okuyucu yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c6a37-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="c6a37-110">GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a37-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="c6a37-111">Sağlanan belgede satırı bilgileri içeren her yöntem alır.</span><span class="sxs-lookup"><span data-stu-id="c6a37-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="c6a37-112">GetSymAttributePreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6a37-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="c6a37-113">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="c6a37-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6a37-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6a37-114">Requirements</span></span>  
 <span data-ttu-id="c6a37-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c6a37-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a37-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6a37-116">See Also</span></span>  
 [<span data-ttu-id="c6a37-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c6a37-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="c6a37-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6a37-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
