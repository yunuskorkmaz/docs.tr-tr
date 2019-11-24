---
title: ISymUnmanagedDocument Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: 3fa7b6b19d81e374cdb09b07ec181a7f4249a5eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449099"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="c1ddc-102">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="c1ddc-103">Represents a document referenced by a symbol store.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="c1ddc-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="c1ddc-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="c1ddc-106">You can store the document source in the symbol store and retrieve it through this interface.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1ddc-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1ddc-107">Methods</span></span>  
  
|<span data-ttu-id="c1ddc-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c1ddc-108">Method</span></span>|<span data-ttu-id="c1ddc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1ddc-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1ddc-110">FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="c1ddc-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="c1ddc-112">GetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="c1ddc-113">Gets the checksum.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="c1ddc-114">GetCheckSumAlgorithmId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="c1ddc-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="c1ddc-116">GetDocumentType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="c1ddc-117">Gets the document type of this document.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="c1ddc-118">GetLanguage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="c1ddc-119">Gets the language identifier of this document.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="c1ddc-120">GetLanguageVendor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="c1ddc-121">Gets the language vendor of this document.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="c1ddc-122">GetSourceLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="c1ddc-123">Gets the length, in bytes, of the embedded source.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="c1ddc-124">GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="c1ddc-125">Returns the specified range of the embedded source into the given buffer.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="c1ddc-126">GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="c1ddc-127">Returns the URL for this document.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="c1ddc-128">HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ddc-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="c1ddc-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1ddc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1ddc-130">See also</span></span>

- [<span data-ttu-id="c1ddc-131">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1ddc-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
