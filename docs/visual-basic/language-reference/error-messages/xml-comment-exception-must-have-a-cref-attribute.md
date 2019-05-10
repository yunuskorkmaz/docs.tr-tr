---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 91bde92e2184c90b14838a09a89a6d261447f139
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662606"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="1ce66-102">XML açıklama özel durumunda 'cref' özniteliği olmalıdır</span><span class="sxs-lookup"><span data-stu-id="1ce66-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="1ce66-103">\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ce66-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="1ce66-104">Gerekli `cref` öznitelik belgeleri Oluşturucu tarafından denetlenir bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ce66-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="1ce66-105">Üye varsa, kurallı öğe adı belgeleri dosyasına çevrilir.</span><span class="sxs-lookup"><span data-stu-id="1ce66-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="1ce66-106">**Hata Kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="1ce66-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ce66-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1ce66-107">To correct this error</span></span>  
  
- <span data-ttu-id="1ce66-108">Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:</span><span class="sxs-lookup"><span data-stu-id="1ce66-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1ce66-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ce66-109">See also</span></span>

- [<span data-ttu-id="1ce66-110">\<Özel Durum ></span><span class="sxs-lookup"><span data-stu-id="1ce66-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="1ce66-111">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ce66-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="1ce66-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="1ce66-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
