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
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709082"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="44f24-102">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44f24-102">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="44f24-103">Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="44f24-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="44f24-104">Bu arabirim [ıstreamunmanagedreader](isymunmanagedreader-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="44f24-104">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44f24-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="44f24-105">Methods</span></span>  
  
|<span data-ttu-id="44f24-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="44f24-106">Method</span></span>|<span data-ttu-id="44f24-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44f24-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44f24-108">GetMethodByVersionPreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44f24-108">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="44f24-109">Bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası verilen bir sembol okuyucu yöntemi alın.</span><span class="sxs-lookup"><span data-stu-id="44f24-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="44f24-110">GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44f24-110">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="44f24-111">Belirtilen belgede satır bilgilerine sahip her yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="44f24-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="44f24-112">GetSymAttributePreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44f24-112">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="44f24-113">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="44f24-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44f24-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44f24-114">Requirements</span></span>  

 <span data-ttu-id="44f24-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="44f24-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f24-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44f24-116">See also</span></span>

- [<span data-ttu-id="44f24-117">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="44f24-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="44f24-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44f24-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
