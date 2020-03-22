---
title: Yapılar ve Diğer Programlama Öğeleri
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 73d3f999e95c484dff3f5409f2cdb9032b64fe38
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266865"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="fff97-102">Yapılar ve Diğer Programlama Öğeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fff97-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="fff97-103">Yapıları diziler, nesneler ve yordamlarla ve birbiriyle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="fff97-104">Etkileşimler, bu öğelerin tek tek kullandığı sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fff97-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fff97-105">Yapı bildirimindeki yapı öğelerinden hiçbirini başharfe agiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="fff97-106">Değerleri yalnızca bir yapı türüne ait olduğu bildirilen bir değişkenin öğelerine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="fff97-107">Yapılar ve Diziler</span><span class="sxs-lookup"><span data-stu-id="fff97-107">Structures and Arrays</span></span>  
 <span data-ttu-id="fff97-108">Bir yapı, bir veya daha fazla öğesi olarak bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fff97-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="fff97-109">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="fff97-110">Bir nesnedeki bir özelliğe eriştiğin gibi bir yapı içindeki dizinin değerlerine erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="fff97-111">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="fff97-112">Bir dizi yapıyı da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-112">You can also declare an array of structures.</span></span> <span data-ttu-id="fff97-113">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="fff97-114">Bu veri mimarisinin bileşenlerine erişmek için aynı kurallara uyarsınız.</span><span class="sxs-lookup"><span data-stu-id="fff97-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="fff97-115">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="fff97-116">Yapılar ve Nesneler</span><span class="sxs-lookup"><span data-stu-id="fff97-116">Structures and Objects</span></span>  
 <span data-ttu-id="fff97-117">Bir yapı, bir nesneyi bir veya daha fazla öğe olarak içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fff97-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="fff97-118">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="fff97-119">Böyle bir bildirimde belirli bir nesne sınıfı `Object`yerine kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="fff97-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="fff97-120">Yapı ve Prosedürler</span><span class="sxs-lookup"><span data-stu-id="fff97-120">Structures and Procedures</span></span>  
 <span data-ttu-id="fff97-121">Bir yapıyı yordam bağımsız değişkeni olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="fff97-122">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="fff97-123">Önceki örnek, yordamın öğelerini değiştirmesini sağlayan, arama kodunda değişikliklerin etkili olmasını sağlayan yapıyı *referansla*geçirir.</span><span class="sxs-lookup"><span data-stu-id="fff97-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="fff97-124">Bir yapıyı bu tür değişikliklere karşı korumak istiyorsanız, değerine göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="fff97-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="fff97-125">Ayrıca bir `Function` yordamdan bir yapı döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="fff97-126">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="fff97-127">Yapıların İçindeki Yapılar</span><span class="sxs-lookup"><span data-stu-id="fff97-127">Structures Within Structures</span></span>  
 <span data-ttu-id="fff97-128">Yapılar başka yapılar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fff97-128">Structures can contain other structures.</span></span> <span data-ttu-id="fff97-129">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fff97-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="fff97-130">Ayrıca, farklı bir modülde tanımlanan bir yapı içinde tek bir modülde tanımlanan bir yapıyı kapsüllemek için de bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff97-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="fff97-131">Yapılar rasgele bir derinliğe diğer yapıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fff97-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff97-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fff97-132">See also</span></span>

- [<span data-ttu-id="fff97-133">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fff97-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="fff97-134">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fff97-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="fff97-135">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fff97-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="fff97-136">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="fff97-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="fff97-137">Yapılar</span><span class="sxs-lookup"><span data-stu-id="fff97-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="fff97-138">Veri Türleri Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="fff97-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="fff97-139">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="fff97-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="fff97-140">Yapı Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="fff97-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="fff97-141">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="fff97-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="fff97-142">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="fff97-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
