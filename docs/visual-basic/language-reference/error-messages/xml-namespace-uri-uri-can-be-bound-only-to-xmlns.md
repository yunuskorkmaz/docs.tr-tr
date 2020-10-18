---
title: XML as alanı URI’si '<uri>' yalnızca 'xmlns' ile bağlanabilir
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: 1aec6ac0a354bfe7e0378a2e46a70a7161bf6d36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163252"
---
# <a name="bc31183-xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a><span data-ttu-id="c6dec-102">BC31183: XML ad alanı URI `http://www.w3.org/XML/1998/namespace` ; yalnızca ' xmlns ' öğesine bağlanabilir</span><span class="sxs-lookup"><span data-stu-id="c6dec-102">BC31183: XML namespace URI `http://www.w3.org/XML/1998/namespace`; can be bound only to 'xmlns'</span></span>

<span data-ttu-id="c6dec-103">URI, `http://www.w3.org/XML/1998/namespace` BIR XML ad alanı bildiriminde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6dec-103">The URI `http://www.w3.org/XML/1998/namespace` is used in an XML namespace declaration.</span></span> <span data-ttu-id="c6dec-104">Bu URI ayrılmış bir ad alanıdır ve bir XML ad alanı bildirimine dahil edilemez.</span><span class="sxs-lookup"><span data-stu-id="c6dec-104">This URI is a reserved namespace and cannot be included in an XML namespace declaration.</span></span>

 <span data-ttu-id="c6dec-105">**Hata kimliği:** BC31183</span><span class="sxs-lookup"><span data-stu-id="c6dec-105">**Error ID:** BC31183</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c6dec-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c6dec-106">To correct this error</span></span>

<span data-ttu-id="c6dec-107">XML ad alanı bildirimini kaldırın veya URI `http://www.w3.org/XML/1998/namespace` 'yi geçerli bir ad alanı URI 'si ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c6dec-107">Remove the XML namespace declaration or replace the URI `http://www.w3.org/XML/1998/namespace` with a valid namespace URI.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6dec-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6dec-108">See also</span></span>

- [<span data-ttu-id="c6dec-109">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="c6dec-109">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="c6dec-110">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="c6dec-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="c6dec-111">XML</span><span class="sxs-lookup"><span data-stu-id="c6dec-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
