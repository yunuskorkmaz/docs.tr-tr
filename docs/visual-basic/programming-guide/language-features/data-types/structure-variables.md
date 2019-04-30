---
title: Yapı Değişkenleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663394"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="a0192-102">Yapı Değişkenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0192-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="a0192-103">Bir yapı oluşturulduktan sonra bu türü olarak yordam ve Modül düzeyinde değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0192-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="a0192-104">Örneğin, bir bilgisayar sistemi ilgili bilgileri kaydeden bir yapısı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0192-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="a0192-105">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0192-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="a0192-106">Artık, değişkenlerini türü bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0192-106">You can now declare variables of that type.</span></span> <span data-ttu-id="a0192-107">Aşağıdaki bildirimi bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a0192-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="a0192-108">Yapıları sınıflar ve modüller, kullanılarak bildirilen [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) varsayılan genel erişim için.</span><span class="sxs-lookup"><span data-stu-id="a0192-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="a0192-109">Bir yapı özel olmasını istiyorsanız'ı kullanarak bildirdiğinizden emin olun [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a0192-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="a0192-110">Yapı değerlerine erişim</span><span class="sxs-lookup"><span data-stu-id="a0192-110">Access to Structure Values</span></span>  
 <span data-ttu-id="a0192-111">Atamak ve bir yapı değişkenin öğeleri değerleri almak için bir nesne üzerinde özelliklerini alma ve ayarlamak için kullandığınız aynı sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0192-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="a0192-112">Üye erişimi işleci yerleştirin (`.`) değişkenin adını yapı arasındaki öğe adı.</span><span class="sxs-lookup"><span data-stu-id="a0192-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="a0192-113">Aşağıdaki örnekte önceden türü olarak bildirilmiş değişkenlerin öğeleri erişen `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="a0192-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="a0192-114">Yapı değişkenleri atama</span><span class="sxs-lookup"><span data-stu-id="a0192-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="a0192-115">Her ikisi de aynı yapı türü olduğunda, ayrıca bir değişken diğerine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0192-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="a0192-116">Bu, bir yapının tüm öğeleri karşılık gelen öğelerle diğer kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a0192-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="a0192-117">Aşağıdaki bildirimi bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a0192-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="a0192-118">Yapı öğesi bir başvuru türü olduğu gibi bir `String`, `Object`, ya da veri işaretçisine diziye kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="a0192-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="a0192-119">Önceki örnekte, `systemInfo` sonra kopyalanan işaretçisinden önceki örnekte bir nesne değişkeninin dahil `mySystem` için `yourSystem`, ve bir değişiklik nesne verilerinin bir yapısı üzerinden erişildiğinde yürürlükte olur diğer yapısı.</span><span class="sxs-lookup"><span data-stu-id="a0192-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0192-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0192-120">See also</span></span>

- [<span data-ttu-id="a0192-121">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a0192-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="a0192-122">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a0192-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="a0192-123">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a0192-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="a0192-124">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="a0192-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="a0192-125">Yapılar</span><span class="sxs-lookup"><span data-stu-id="a0192-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a0192-126">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="a0192-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="a0192-127">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="a0192-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a0192-128">Yapılar ve Diğer Programlama Öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0192-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="a0192-129">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="a0192-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="a0192-130">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0192-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
