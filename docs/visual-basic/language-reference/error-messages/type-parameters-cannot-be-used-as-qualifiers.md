---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: ba7348ae50965ffcf2719b20934451916c8fa95a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296361"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="47e09-102">Tür parametreleri niteleyici olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="47e09-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="47e09-103">Bir programlama öğesi bir tür parametresi içeren bir nitelik dizesiyle nitelenmiş.</span><span class="sxs-lookup"><span data-stu-id="47e09-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="47e09-104">Bir tür parametresi, genel tür oluşturulduğunda sağlanacak olan bir türü için bir gereksinimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="47e09-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="47e09-105">Tanımlanmış bir türü göstermiyor.</span><span class="sxs-lookup"><span data-stu-id="47e09-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="47e09-106">Bir nitelik dize, derleme zamanında tanımlanan öğeler içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="47e09-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="47e09-107">Aşağıdaki deyimleri, bu hata oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47e09-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="47e09-108">**Hata Kimliği:** BC32098</span><span class="sxs-lookup"><span data-stu-id="47e09-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47e09-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="47e09-109">To correct this error</span></span>  
  
1. <span data-ttu-id="47e09-110">Tür parametresi nitelik dizeden kaldırın veya tanımlanan bir tür ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="47e09-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2. <span data-ttu-id="47e09-111">Oluşturulan tür nitelendirme programlama öğesine bulmak için kullanmanız gerekiyorsa, ek bir programın mantığı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47e09-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e09-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47e09-112">See also</span></span>

- [<span data-ttu-id="47e09-113">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="47e09-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="47e09-114">Visual Basic'de Genel Türler</span><span class="sxs-lookup"><span data-stu-id="47e09-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="47e09-115">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="47e09-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
