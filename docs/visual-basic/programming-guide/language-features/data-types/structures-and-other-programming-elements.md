---
title: "Yapılar ve Diğer Programlama Öğeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de343c06ec255d6cb68aa25d733e85385e884769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="a2e1a-102">Yapılar ve Diğer Programlama Öğeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e1a-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="a2e1a-103">Diziler, nesneleri ve yordamlarla yanı sıra birbirleri ile birlikte yapıları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="a2e1a-104">Bu öğeleri tek tek kullandıkça etkileşimler aynı sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2e1a-105">Yapı bildirimleri yapısı öğelerinde başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="a2e1a-106">Yalnızca bir yapı türüne sahip olması için bildirilen bir değişken öğelerine değerler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="a2e1a-107">Yapılar ve diziler</span><span class="sxs-lookup"><span data-stu-id="a2e1a-107">Structures and Arrays</span></span>  
 <span data-ttu-id="a2e1a-108">Bir yapı bir dizi olarak bir veya daha fazla öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="a2e1a-109">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="a2e1a-110">Bir nesne üzerinde bir özellik erişim aynı şekilde bir yapısı içinde bir dizi değerlerini erişin.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="a2e1a-111">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="a2e1a-112">Bir dizi yapıları da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-112">You can also declare an array of structures.</span></span> <span data-ttu-id="a2e1a-113">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="a2e1a-114">Bu veri mimarisi bileşenlerine erişmek için aynı kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="a2e1a-115">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="a2e1a-116">Yapılar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="a2e1a-116">Structures and Objects</span></span>  
 <span data-ttu-id="a2e1a-117">Bir yapı bir nesne olarak bir veya daha fazla öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="a2e1a-118">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="a2e1a-119">Bu tür bildiriminde belirli nesne sınıfını kullanmalısınız yerine `Object`.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="a2e1a-120">Yapılar ve yordamları</span><span class="sxs-lookup"><span data-stu-id="a2e1a-120">Structures and Procedures</span></span>  
 <span data-ttu-id="a2e1a-121">Bir yordam bağımsız değişkeni bir yapı geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="a2e1a-122">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="a2e1a-123">Önceki örnekte yapısı geçirir *başvuruya göre*, yordamın öğeleri arama kodda değişiklikler etkili şekilde değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="a2e1a-124">Bu tür değişiklik karşı bir yapı korumak istiyorsanız, tarafından değerini geçirin.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="a2e1a-125">Ayrıca bir yapısından dönebilirsiniz bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="a2e1a-126">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="a2e1a-127">Yapıları içindeki yapıları</span><span class="sxs-lookup"><span data-stu-id="a2e1a-127">Structures Within Structures</span></span>  
 <span data-ttu-id="a2e1a-128">Yapıları diğer yapıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-128">Structures can contain other structures.</span></span> <span data-ttu-id="a2e1a-129">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="a2e1a-130">Bu yöntem, bir modülü farklı bir modülde tanımlanmış bir yapı içinde tanımlanmış bir yapı kapsüllemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="a2e1a-131">Yapıları rasgele derinliği diğer yapıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e1a-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e1a-132">See Also</span></span>  
 [<span data-ttu-id="a2e1a-133">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="a2e1a-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="a2e1a-134">Başlangıç veri türleri</span><span class="sxs-lookup"><span data-stu-id="a2e1a-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="a2e1a-135">Bileşik veri türleri</span><span class="sxs-lookup"><span data-stu-id="a2e1a-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="a2e1a-136">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="a2e1a-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="a2e1a-137">Yapıları</span><span class="sxs-lookup"><span data-stu-id="a2e1a-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="a2e1a-138">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="a2e1a-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="a2e1a-139">Nasıl yapılır: bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="a2e1a-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="a2e1a-140">Yapı değişkenleri</span><span class="sxs-lookup"><span data-stu-id="a2e1a-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="a2e1a-141">Yapılar ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="a2e1a-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="a2e1a-142">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="a2e1a-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
