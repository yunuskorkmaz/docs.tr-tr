---
description: 'Daha fazla bilgi edinin: ISymUnmanagedReader2 Interface'
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
ms.openlocfilehash: 2e6d994a3252b7fb09b2915266e3142255878a88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763624"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="54e02-103">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e02-103">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="54e02-104">Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54e02-104">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="54e02-105">Bu arabirim [ıstreamunmanagedreader](isymunmanagedreader-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="54e02-105">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54e02-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="54e02-106">Methods</span></span>  
  
|<span data-ttu-id="54e02-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="54e02-107">Method</span></span>|<span data-ttu-id="54e02-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e02-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54e02-109">GetMethodByVersionPreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54e02-109">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="54e02-110">Bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası verilen bir sembol okuyucu yöntemi alın.</span><span class="sxs-lookup"><span data-stu-id="54e02-110">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="54e02-111">GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54e02-111">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="54e02-112">Belirtilen belgede satır bilgilerine sahip her yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="54e02-112">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="54e02-113">GetSymAttributePreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54e02-113">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="54e02-114">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="54e02-114">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54e02-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54e02-115">Requirements</span></span>  

 <span data-ttu-id="54e02-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="54e02-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e02-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e02-117">See also</span></span>

- [<span data-ttu-id="54e02-118">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="54e02-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="54e02-119">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e02-119">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
