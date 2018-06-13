---
title: Yapı Değişkenleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 0dad7bdcac5428753e252f3b26ca0a127c293a7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648505"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="00437-102">Yapı Değişkenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00437-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="00437-103">Bir yapı oluşturduktan sonra bu tür olarak yordamı ve modül düzeyi değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00437-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="00437-104">Örneğin, bir bilgisayar sistemi ilgili bilgileri kaydeden bir yapı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00437-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="00437-105">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="00437-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="00437-106">Bu tür değişkenler şimdi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00437-106">You can now declare variables of that type.</span></span> <span data-ttu-id="00437-107">Aşağıdaki bildirimi bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="00437-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="00437-108">Sınıfları ve modülleri, yapıları bildirilen kullanarak [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) varsayılan olarak genel erişim.</span><span class="sxs-lookup"><span data-stu-id="00437-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="00437-109">Özel olarak bir yapı düşünüyorsanız, bildirdiğiniz kullanarak emin olun [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="00437-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="00437-110">Yapı değerleri erişimi</span><span class="sxs-lookup"><span data-stu-id="00437-110">Access to Structure Values</span></span>  
 <span data-ttu-id="00437-111">Atamak ve bir yapı değişkenin öğeleri değerleri almak için ayarlamak ve nesne özellikleri elde etmek için kullandığınız aynı sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="00437-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="00437-112">Üye erişimi işleci yerleştirin (`.`) arasında yapısı değişken adını ve öğe adı.</span><span class="sxs-lookup"><span data-stu-id="00437-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="00437-113">Aşağıdaki örnek daha önce türü olarak bildirilen değişkenlerin öğeleri erişen `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="00437-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="00437-114">Yapı değişkenleri atama</span><span class="sxs-lookup"><span data-stu-id="00437-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="00437-115">Her ikisi de aynı yapısı türde olduğunda, aynı zamanda bir değişken diğerine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00437-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="00437-116">Bu diğer karşılık gelen öğe bir yapısının tüm öğeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="00437-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="00437-117">Aşağıdaki bildirimi bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="00437-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="00437-118">Yapı öğesi bir başvuru türü gibi ise bir `String`, `Object`, veya dizi, verileri işaretçisine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="00437-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="00437-119">Önceki örnekte, `systemInfo` önceki örnekte işaretçi kopyaladığınız sonra bir nesne değişkeni dahil `mySystem` için `yourSystem`, ve bir yapı nesnenin verilerine bir değişiklik erişildiğinde etkili olacaktır diğer yapısı.</span><span class="sxs-lookup"><span data-stu-id="00437-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00437-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00437-120">See Also</span></span>  
 [<span data-ttu-id="00437-121">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="00437-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="00437-122">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="00437-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="00437-123">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="00437-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="00437-124">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="00437-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="00437-125">Yapılar</span><span class="sxs-lookup"><span data-stu-id="00437-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="00437-126">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="00437-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="00437-127">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="00437-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="00437-128">Yapılar ve Diğer Programlama Öğeleri</span><span class="sxs-lookup"><span data-stu-id="00437-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="00437-129">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="00437-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="00437-130">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="00437-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
