---
title: "Tür parametreleri niteleyici olarak kullanılamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="c09e7-102">Tür parametreleri niteleyici olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="c09e7-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="c09e7-103">Bir programlama öğesi bir tür parametresi içeren bir niteliği dizeyle tam.</span><span class="sxs-lookup"><span data-stu-id="c09e7-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="c09e7-104">Tür parametresi genel türü oluşturulduğunda sağlanacak olan bir türü gereksinimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c09e7-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="c09e7-105">Belirli tanımlanmış bir türü göstermiyor.</span><span class="sxs-lookup"><span data-stu-id="c09e7-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="c09e7-106">Niteliğe dize derleme zamanında tanımlanan öğeleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c09e7-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="c09e7-107">Aşağıdaki deyimleri bu hata oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c09e7-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="c09e7-108">**Hata Kimliği:** BC32098</span><span class="sxs-lookup"><span data-stu-id="c09e7-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c09e7-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c09e7-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="c09e7-110">Tür parametresi niteliğe dizeden kaldırın veya tanımlanmış bir türü ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c09e7-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="c09e7-111">Tamamlandıktan programlama öğesi bulmak için yapılandırılmış bir tür kullanmanız gerekiyorsa, ek program mantığı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c09e7-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09e7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c09e7-112">See Also</span></span>  
 [<span data-ttu-id="c09e7-113">Bildirilmiş öğelere başvurular</span><span class="sxs-lookup"><span data-stu-id="c09e7-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="c09e7-114">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="c09e7-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="c09e7-115">Tür listesi</span><span class="sxs-lookup"><span data-stu-id="c09e7-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
