---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader arabirimi'
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
ms.openlocfilehash: bad4fdbac3bf6f03fa0db79ce54a5b0ca897028f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763806"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="0c6e4-103">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-103">ISymUnmanagedReader Interface</span></span>

<span data-ttu-id="0c6e4-104">Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-104">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c6e4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0c6e4-105">Methods</span></span>  
  
|<span data-ttu-id="0c6e4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0c6e4-106">Method</span></span>|<span data-ttu-id="0c6e4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c6e4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c6e4-108">GetDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-108">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="0c6e4-109">Bir belge bulur.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-109">Finds a document.</span></span>|  
|[<span data-ttu-id="0c6e4-110">GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-110">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="0c6e4-111">Sembol deposunda tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-111">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="0c6e4-112">GetDocumentVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-112">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="0c6e4-113">Belirtilen belgenin belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-113">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="0c6e4-114">GetGlobalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-114">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="0c6e4-115">Tüm genel değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-115">Returns all global variables.</span></span>|  
|[<span data-ttu-id="0c6e4-116">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-116">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="0c6e4-117">Yöntem belirteci verilen bir sembol okuyucu yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-117">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="0c6e4-118">GetMethodByVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-118">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="0c6e4-119">Yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-119">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="0c6e4-120">GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-120">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="0c6e4-121">Bir belgede verilen konumdaki kesme noktasını içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-121">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="0c6e4-122">GetMethodsFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-122">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="0c6e4-123">Her biri bir belgede verilen konumdaki kesme noktasını içeren bir yöntem dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-123">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="0c6e4-124">GetMethodVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-124">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="0c6e4-125">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-125">Gets the method version.</span></span>|  
|[<span data-ttu-id="0c6e4-126">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-126">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="0c6e4-127">Bu sembol deposu içindeki genel kapsamda tanımlanan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-127">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="0c6e4-128">GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-128">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="0c6e4-129">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-129">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="0c6e4-130">GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-130">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="0c6e4-131">Sembol deposunun disk üzerindeki dosya adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-131">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="0c6e4-132">GetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-132">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="0c6e4-133">Varsa modül için Kullanıcı giriş noktası olarak belirtilen yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-133">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="0c6e4-134">GetVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-134">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="0c6e4-135">Üst ve adı verilen yerel olmayan bir değişken döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-135">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="0c6e4-136">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-136">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="0c6e4-137">Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-137">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="0c6e4-138">ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-138">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="0c6e4-139">Var olan sembol deposunu bir Delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-139">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="0c6e4-140">UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-140">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="0c6e4-141">Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-141">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c6e4-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c6e4-142">Requirements</span></span>  

 <span data-ttu-id="0c6e4-143">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0c6e4-143">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6e4-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c6e4-144">See also</span></span>

- [<span data-ttu-id="0c6e4-145">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c6e4-145">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0c6e4-146">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c6e4-146">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
