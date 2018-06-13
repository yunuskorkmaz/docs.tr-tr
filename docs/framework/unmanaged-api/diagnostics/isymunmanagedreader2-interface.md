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
ms.openlocfilehash: 1dfc67ecf1eeb9ea5a19c98a8c378e73021da6c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426834"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="faae0-102">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faae0-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="faae0-103">Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="faae0-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="faae0-104">Bu arabirim genişletir [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="faae0-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="faae0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="faae0-105">Methods</span></span>  
  
|<span data-ttu-id="faae0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="faae0-106">Method</span></span>|<span data-ttu-id="faae0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="faae0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="faae0-108">GetMethodByVersionPreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faae0-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="faae0-109">Verilen bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası alma simgesi okuyucu yöntemi.</span><span class="sxs-lookup"><span data-stu-id="faae0-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="faae0-110">GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faae0-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="faae0-111">Sağlanan belgede satırı bilgileri içeren her yöntem alır.</span><span class="sxs-lookup"><span data-stu-id="faae0-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="faae0-112">GetSymAttributePreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faae0-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="faae0-113">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="faae0-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faae0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faae0-114">Requirements</span></span>  
 <span data-ttu-id="faae0-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="faae0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faae0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="faae0-116">See Also</span></span>  
 [<span data-ttu-id="faae0-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="faae0-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="faae0-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faae0-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
