---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406514"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="d7f6c-102">XML açıklama özel durumunda 'cref' özniteliği olmalıdır</span><span class="sxs-lookup"><span data-stu-id="d7f6c-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="d7f6c-103">\<exception>Etiketi, bir yöntem tarafından oluşturulan özel durumları belgelemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7f6c-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="d7f6c-104">Gerekli `cref` öznitelik, belge Oluşturucu tarafından denetlenen bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7f6c-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="d7f6c-105">Üye varsa, belge dosyasında kurallı öğe adına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="d7f6c-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="d7f6c-106">**Hata kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="d7f6c-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d7f6c-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d7f6c-107">To correct this error</span></span>

<span data-ttu-id="d7f6c-108">`cref`Özel duruma şu şekilde özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d7f6c-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="d7f6c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7f6c-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="d7f6c-110">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7f6c-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="d7f6c-111">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d7f6c-111">XML Comment Tags</span></span>](../xmldoc/index.md)
