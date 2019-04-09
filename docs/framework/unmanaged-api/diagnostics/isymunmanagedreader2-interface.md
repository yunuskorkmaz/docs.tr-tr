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
ms.openlocfilehash: 890053e1bf2e0648a41cca718e94edcf21c7e612
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165990"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="94857-102">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94857-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="94857-103">Belgeler, yöntemler ve değişkenler bir sembol deposundaki erişim sağlayan bir sembol okuyucu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="94857-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="94857-104">Bu arabirim genişletir [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="94857-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94857-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="94857-105">Methods</span></span>  
  
|<span data-ttu-id="94857-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94857-106">Method</span></span>|<span data-ttu-id="94857-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94857-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94857-108">GetMethodByVersionPreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94857-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="94857-109">Bir sembol okuyucu yöntemi verilen token metody ve bir Düzenle ve devam et sürüm numarasını alın.</span><span class="sxs-lookup"><span data-stu-id="94857-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="94857-110">GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94857-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="94857-111">Sağlanan belge içinde satır bilgileri her yöntemin alır.</span><span class="sxs-lookup"><span data-stu-id="94857-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="94857-112">GetSymAttributePreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94857-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="94857-113">Özel bir öznitelik adı üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="94857-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94857-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94857-114">Requirements</span></span>  
 <span data-ttu-id="94857-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94857-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94857-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94857-116">See also</span></span>

- [<span data-ttu-id="94857-117">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94857-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="94857-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94857-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
