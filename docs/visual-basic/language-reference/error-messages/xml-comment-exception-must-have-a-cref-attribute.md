---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321168"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="e5ca3-102">XML açıklama özel durumunda 'cref' özniteliği olmalıdır</span><span class="sxs-lookup"><span data-stu-id="e5ca3-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="e5ca3-103">@No__t-0exception > etiketi, bir yöntem tarafından oluşturulan özel durumları belgelemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="e5ca3-104">Gerekli `cref` özniteliği, belge Oluşturucu tarafından denetlenen bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="e5ca3-105">Üye varsa, belge dosyasında kurallı öğe adına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="e5ca3-106">**Hata kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="e5ca3-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e5ca3-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e5ca3-107">To correct this error</span></span>

<span data-ttu-id="e5ca3-108">@No__t-0 özniteliğini özel duruma aşağıdaki şekilde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5ca3-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="e5ca3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5ca3-109">See also</span></span>

- [<span data-ttu-id="e5ca3-110">\< özel durum ></span><span class="sxs-lookup"><span data-stu-id="e5ca3-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="e5ca3-111">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5ca3-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="e5ca3-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="e5ca3-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
