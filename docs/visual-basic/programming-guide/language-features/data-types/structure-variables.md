---
title: "Yapı Değişkenleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42c44de84caffde909eb2b3e9361016a6abb97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="e102a-102">Yapı Değişkenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e102a-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="e102a-103">Bir yapı oluşturduktan sonra bu tür olarak yordamı ve modül düzeyi değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e102a-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="e102a-104">Örneğin, bir bilgisayar sistemi ilgili bilgileri kaydeden bir yapı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e102a-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="e102a-105">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e102a-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="e102a-106">Bu tür değişkenler şimdi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e102a-106">You can now declare variables of that type.</span></span> <span data-ttu-id="e102a-107">Aşağıdaki bildirimi bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e102a-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="e102a-108">Sınıfları ve modülleri, yapıları bildirilen kullanarak [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) varsayılan olarak genel erişim.</span><span class="sxs-lookup"><span data-stu-id="e102a-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="e102a-109">Özel olarak bir yapı düşünüyorsanız, bildirdiğiniz kullanarak emin olun [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e102a-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="e102a-110">Yapı değerleri erişimi</span><span class="sxs-lookup"><span data-stu-id="e102a-110">Access to Structure Values</span></span>  
 <span data-ttu-id="e102a-111">Atamak ve bir yapı değişkenin öğeleri değerleri almak için ayarlamak ve nesne özellikleri elde etmek için kullandığınız aynı sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e102a-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="e102a-112">Üye erişimi işleci yerleştirin (`.`) arasında yapısı değişken adını ve öğe adı.</span><span class="sxs-lookup"><span data-stu-id="e102a-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="e102a-113">Aşağıdaki örnek daha önce türü olarak bildirilen değişkenlerin öğeleri erişen `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="e102a-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="e102a-114">Yapı değişkenleri atama</span><span class="sxs-lookup"><span data-stu-id="e102a-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="e102a-115">Her ikisi de aynı yapısı türde olduğunda, aynı zamanda bir değişken diğerine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e102a-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="e102a-116">Bu diğer karşılık gelen öğe bir yapısının tüm öğeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e102a-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="e102a-117">Aşağıdaki bildirimi bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e102a-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="e102a-118">Yapı öğesi bir başvuru türü gibi ise bir `String`, `Object`, veya dizi, verileri işaretçisine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="e102a-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="e102a-119">Önceki örnekte, `systemInfo` önceki örnekte işaretçi kopyaladığınız sonra bir nesne değişkeni dahil `mySystem` için `yourSystem`, ve bir yapı nesnenin verilerine bir değişiklik erişildiğinde etkili olacaktır diğer yapısı.</span><span class="sxs-lookup"><span data-stu-id="e102a-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e102a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e102a-120">See Also</span></span>  
 [<span data-ttu-id="e102a-121">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="e102a-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="e102a-122">Başlangıç veri türleri</span><span class="sxs-lookup"><span data-stu-id="e102a-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="e102a-123">Bileşik veri türleri</span><span class="sxs-lookup"><span data-stu-id="e102a-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="e102a-124">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="e102a-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="e102a-125">Yapıları</span><span class="sxs-lookup"><span data-stu-id="e102a-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="e102a-126">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="e102a-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="e102a-127">Nasıl yapılır: bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="e102a-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="e102a-128">Yapılar ve diğer programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="e102a-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="e102a-129">Yapılar ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="e102a-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="e102a-130">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="e102a-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
