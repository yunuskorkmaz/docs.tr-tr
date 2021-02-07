---
description: "Hakkında daha fazla bilgi edinin: BC42319: XML açıklama özel durumu ' cref ' özniteliğine sahip olmalıdır"
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: e602a2973d95f70d5ab532e6be319a9575d239a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701462"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="a4a0a-103">BC42319: XML açıklama özel durumunun ' cref ' özniteliği olmalıdır</span><span class="sxs-lookup"><span data-stu-id="a4a0a-103">BC42319: XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="a4a0a-104">\<exception>Etiketi, bir yöntem tarafından oluşturulan özel durumları belgelemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-104">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="a4a0a-105">Gerekli `cref` öznitelik, belge Oluşturucu tarafından denetlenen bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-105">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="a4a0a-106">Üye varsa, belge dosyasında kurallı öğe adına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-106">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="a4a0a-107">**Hata kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="a4a0a-107">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a4a0a-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a4a0a-108">To correct this error</span></span>

<span data-ttu-id="a4a0a-109">`cref`Özel duruma şu şekilde özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4a0a-109">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="a4a0a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-110">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="a4a0a-111">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4a0a-111">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="a4a0a-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="a4a0a-112">XML Comment Tags</span></span>](../xmldoc/index.md)
