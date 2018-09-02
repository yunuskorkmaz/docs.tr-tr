---
title: XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404771"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="f1ea8-102">XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği</span><span class="sxs-lookup"><span data-stu-id="f1ea8-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="f1ea8-103">\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1ea8-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="f1ea8-104">Gerekli `cref` öznitelik belgeleri Oluşturucu tarafından denetlenir bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1ea8-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="f1ea8-105">Üye varsa, kurallı öğe adı belgeleri dosyasına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="f1ea8-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="f1ea8-106">**Hata Kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="f1ea8-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1ea8-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f1ea8-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f1ea8-108">Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:</span><span class="sxs-lookup"><span data-stu-id="f1ea8-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f1ea8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1ea8-109">See Also</span></span>  
 [<span data-ttu-id="f1ea8-110">\<Özel Durum ></span><span class="sxs-lookup"><span data-stu-id="f1ea8-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="f1ea8-111">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1ea8-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="f1ea8-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="f1ea8-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
