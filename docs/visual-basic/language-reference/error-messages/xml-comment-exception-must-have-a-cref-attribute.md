---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592036"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="27462-102">XML açıklama özel durumunda 'cref' özniteliği olmalıdır</span><span class="sxs-lookup"><span data-stu-id="27462-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="27462-103">@No__t-0exception > etiketi, bir yöntem tarafından oluşturulan özel durumları belgelemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="27462-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="27462-104">Gerekli `cref` özniteliği, belge Oluşturucu tarafından denetlenen bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="27462-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="27462-105">Üye varsa, belge dosyasında kurallı öğe adına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="27462-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="27462-106">**Hata KIMLIĞI:** BC42319</span><span class="sxs-lookup"><span data-stu-id="27462-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27462-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="27462-107">To correct this error</span></span>  
  
- <span data-ttu-id="27462-108">@No__t-0 özniteliğini özel duruma aşağıdaki şekilde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="27462-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    <span data-ttu-id="27462-109">xml</span><span class="sxs-lookup"><span data-stu-id="27462-109">xml</span></span>  
    <span data-ttu-id="27462-110">' ' '<exception cref="member">açıklaması</exception></span><span class="sxs-lookup"><span data-stu-id="27462-110">'''<exception cref="member">description</exception></span></span>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
