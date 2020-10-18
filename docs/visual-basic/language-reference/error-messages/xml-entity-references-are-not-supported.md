---
title: XML varlık başvuruları desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 37e72dbd6de61a50b4192a0151db40cb4be49d1c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163278"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a><span data-ttu-id="3b909-102">BC31180: XML varlık başvuruları desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="3b909-102">BC31180: XML entity references are not supported</span></span>

<span data-ttu-id="3b909-103">XML 1,0 belirtiminde tanımlanmayan bir varlık başvurusu (örneğin, `©` ), BIR XML sabit değeri için değer olarak eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3b909-103">An entity reference (for example, `©`) that is not defined in the XML 1.0 specification is included as a value for an XML literal.</span></span> <span data-ttu-id="3b909-104">`&`XML değişmez değerlerinde yalnızca,,, `"` `<` `>` ve `'` XML varlık başvuruları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3b909-104">Only `&`, `"`, `<`, `>`, and `'` XML entity references are supported in XML literals.</span></span>

 <span data-ttu-id="3b909-105">**Hata kimliği:** BC31180</span><span class="sxs-lookup"><span data-stu-id="3b909-105">**Error ID:** BC31180</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3b909-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3b909-106">To correct this error</span></span>

- <span data-ttu-id="3b909-107">Desteklenmeyen varlık başvurusunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3b909-107">Remove the unsupported entity reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b909-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b909-108">See also</span></span>

- [<span data-ttu-id="3b909-109">XML Değişmez Değerleri ve XML 1.0 Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3b909-109">XML Literals and the XML 1.0 Specification</span></span>](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [<span data-ttu-id="3b909-110">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="3b909-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="3b909-111">XML</span><span class="sxs-lookup"><span data-stu-id="3b909-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
