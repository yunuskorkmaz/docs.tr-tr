---
title: XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 0f276781165e80b2d869da2518dbe34b33085d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649953"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="6d21f-102">XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği</span><span class="sxs-lookup"><span data-stu-id="6d21f-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="6d21f-103">\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d21f-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="6d21f-104">Gerekli `cref` öznitelik belgeleri Oluşturucu tarafından denetlenir bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d21f-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="6d21f-105">Üye varsa, kurallı öğe adı belgeleri dosyasına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="6d21f-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="6d21f-106">**Hata Kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="6d21f-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d21f-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6d21f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="6d21f-108">Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:</span><span class="sxs-lookup"><span data-stu-id="6d21f-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6d21f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d21f-109">See also</span></span>
- [<span data-ttu-id="6d21f-110">\<Özel Durum ></span><span class="sxs-lookup"><span data-stu-id="6d21f-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="6d21f-111">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d21f-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="6d21f-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="6d21f-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
