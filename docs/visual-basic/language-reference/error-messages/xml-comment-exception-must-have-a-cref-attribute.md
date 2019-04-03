---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a974df5d2305b88946981d0d258a8088b23d3fc3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813294"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="d5d26-102">XML açıklama özel durumunda 'cref' özniteliği olmalıdır</span><span class="sxs-lookup"><span data-stu-id="d5d26-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="d5d26-103">\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5d26-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="d5d26-104">Gerekli `cref` öznitelik belgeleri Oluşturucu tarafından denetlenir bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5d26-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="d5d26-105">Üye varsa, kurallı öğe adı belgeleri dosyasına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="d5d26-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="d5d26-106">**Hata Kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="d5d26-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5d26-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d5d26-107">To correct this error</span></span>  
  
-   <span data-ttu-id="d5d26-108">Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:</span><span class="sxs-lookup"><span data-stu-id="d5d26-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d5d26-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5d26-109">See also</span></span>

- [<span data-ttu-id="d5d26-110">\<Özel Durum ></span><span class="sxs-lookup"><span data-stu-id="d5d26-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="d5d26-111">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5d26-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="d5d26-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d5d26-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
