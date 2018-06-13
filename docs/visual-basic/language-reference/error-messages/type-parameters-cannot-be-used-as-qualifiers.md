---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 563010efc4f3049d330ee2b38b7f59e23292e630
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595154"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="955c8-102">Tür parametreleri niteleyici olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="955c8-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="955c8-103">Bir programlama öğesi bir tür parametresi içeren bir niteliği dizeyle tam.</span><span class="sxs-lookup"><span data-stu-id="955c8-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="955c8-104">Tür parametresi genel türü oluşturulduğunda sağlanacak olan bir türü gereksinimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="955c8-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="955c8-105">Belirli tanımlanmış bir türü göstermiyor.</span><span class="sxs-lookup"><span data-stu-id="955c8-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="955c8-106">Niteliğe dize derleme zamanında tanımlanan öğeleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="955c8-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="955c8-107">Aşağıdaki deyimleri bu hata oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="955c8-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="955c8-108">**Hata Kimliği:** BC32098</span><span class="sxs-lookup"><span data-stu-id="955c8-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="955c8-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="955c8-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="955c8-110">Tür parametresi niteliğe dizeden kaldırın veya tanımlanmış bir türü ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="955c8-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="955c8-111">Tamamlandıktan programlama öğesi bulmak için yapılandırılmış bir tür kullanmanız gerekiyorsa, ek program mantığı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="955c8-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955c8-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="955c8-112">See Also</span></span>  
 [<span data-ttu-id="955c8-113">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="955c8-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="955c8-114">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="955c8-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="955c8-115">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="955c8-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
