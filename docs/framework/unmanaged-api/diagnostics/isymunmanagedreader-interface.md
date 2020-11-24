---
title: ISymUnmanagedReader Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: bca84fdba575ed9bfe572b9fd7a5869620962de6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675873"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="f50f6-102">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f50f6-102">ISymUnmanagedReader Interface</span></span>

<span data-ttu-id="f50f6-103">Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f50f6-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f50f6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f50f6-104">Methods</span></span>  
  
|<span data-ttu-id="f50f6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f50f6-105">Method</span></span>|<span data-ttu-id="f50f6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f50f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f50f6-107">GetDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-107">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="f50f6-108">Bir belge bulur.</span><span class="sxs-lookup"><span data-stu-id="f50f6-108">Finds a document.</span></span>|  
|[<span data-ttu-id="f50f6-109">GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-109">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="f50f6-110">Sembol deposunda tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f50f6-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="f50f6-111">GetDocumentVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-111">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="f50f6-112">Belirtilen belgenin belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="f50f6-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="f50f6-113">GetGlobalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-113">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="f50f6-114">Tüm genel değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="f50f6-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="f50f6-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-115">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="f50f6-116">Yöntem belirteci verilen bir sembol okuyucu yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="f50f6-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="f50f6-117">GetMethodByVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-117">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="f50f6-118">Yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="f50f6-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="f50f6-119">GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-119">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="f50f6-120">Bir belgede verilen konumdaki kesme noktasını içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f50f6-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="f50f6-121">GetMethodsFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-121">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="f50f6-122">Her biri bir belgede verilen konumdaki kesme noktasını içeren bir yöntem dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f50f6-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="f50f6-123">GetMethodVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-123">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="f50f6-124">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="f50f6-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="f50f6-125">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-125">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="f50f6-126">Bu sembol deposu içindeki genel kapsamda tanımlanan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="f50f6-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="f50f6-127">GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-127">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="f50f6-128">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="f50f6-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="f50f6-129">GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-129">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="f50f6-130">Sembol deposunun disk üzerindeki dosya adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f50f6-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="f50f6-131">GetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-131">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="f50f6-132">Varsa modül için Kullanıcı giriş noktası olarak belirtilen yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f50f6-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="f50f6-133">GetVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-133">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="f50f6-134">Üst ve adı verilen yerel olmayan bir değişken döndürür.</span><span class="sxs-lookup"><span data-stu-id="f50f6-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="f50f6-135">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-135">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="f50f6-136">Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.</span><span class="sxs-lookup"><span data-stu-id="f50f6-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="f50f6-137">ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-137">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="f50f6-138">Var olan sembol deposunu bir Delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f50f6-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="f50f6-139">UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f50f6-139">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="f50f6-140">Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f50f6-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f50f6-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f50f6-141">Requirements</span></span>  

 <span data-ttu-id="f50f6-142">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f50f6-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50f6-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f50f6-143">See also</span></span>

- [<span data-ttu-id="f50f6-144">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f50f6-144">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f50f6-145">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f50f6-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
