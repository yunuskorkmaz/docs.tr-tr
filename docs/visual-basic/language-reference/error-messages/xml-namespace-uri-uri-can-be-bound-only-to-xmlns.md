---
description: "Hakkında daha fazla bilgi edinin: BC31183: XML ad alanı URI 'SI `http://www.w3.org/XML/1998/namespace` ; yalnızca ' xmlns 'ye bağlanabilir"
title: XML as alanı URI’si '<uri>' yalnızca 'xmlns' ile bağlanabilir
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: e6a552f4754a12b8e80e5333232d0c48432f7a63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701397"
---
# <a name="bc31183-xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a><span data-ttu-id="cde4a-103">BC31183: XML ad alanı URI `http://www.w3.org/XML/1998/namespace` ; yalnızca ' xmlns ' öğesine bağlanabilir</span><span class="sxs-lookup"><span data-stu-id="cde4a-103">BC31183: XML namespace URI `http://www.w3.org/XML/1998/namespace`; can be bound only to 'xmlns'</span></span>

<span data-ttu-id="cde4a-104">URI, `http://www.w3.org/XML/1998/namespace` BIR XML ad alanı bildiriminde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cde4a-104">The URI `http://www.w3.org/XML/1998/namespace` is used in an XML namespace declaration.</span></span> <span data-ttu-id="cde4a-105">Bu URI ayrılmış bir ad alanıdır ve bir XML ad alanı bildirimine dahil edilemez.</span><span class="sxs-lookup"><span data-stu-id="cde4a-105">This URI is a reserved namespace and cannot be included in an XML namespace declaration.</span></span>

 <span data-ttu-id="cde4a-106">**Hata kimliği:** BC31183</span><span class="sxs-lookup"><span data-stu-id="cde4a-106">**Error ID:** BC31183</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cde4a-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cde4a-107">To correct this error</span></span>

<span data-ttu-id="cde4a-108">XML ad alanı bildirimini kaldırın veya URI `http://www.w3.org/XML/1998/namespace` 'yi geçerli bir ad alanı URI 'si ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cde4a-108">Remove the XML namespace declaration or replace the URI `http://www.w3.org/XML/1998/namespace` with a valid namespace URI.</span></span>

## <a name="see-also"></a><span data-ttu-id="cde4a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cde4a-109">See also</span></span>

- [<span data-ttu-id="cde4a-110">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="cde4a-110">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="cde4a-111">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="cde4a-111">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="cde4a-112">XML</span><span class="sxs-lookup"><span data-stu-id="cde4a-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
