---
title: Yapılar ve Diğer Programlama Öğeleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: ed406254435602dcd98bc97716cc88710a470ed1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679597"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="9cd77-102">Yapılar ve Diğer Programlama Öğeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cd77-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="9cd77-103">Yapılar, diziler, nesneleri ve yordamları yanı sıra birbirleri ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cd77-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="9cd77-104">Bu öğeleri ayrı ayrı olarak etkileşimleri aynı sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cd77-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cd77-105">Yapı öğeleri yapısı bildiriminde başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9cd77-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="9cd77-106">Yalnızca yapısı türü olarak bildirilmiş bir değişken öğelerine değerler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cd77-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="9cd77-107">Yapıları ve diziler</span><span class="sxs-lookup"><span data-stu-id="9cd77-107">Structures and Arrays</span></span>  
 <span data-ttu-id="9cd77-108">Bir yapının bir veya daha fazla alt öğeleri olarak bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="9cd77-109">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="9cd77-110">Bir yapı içinde bir dizi değerlerini, bir nesne üzerinde bir özelliği aynı şekilde erişin.</span><span class="sxs-lookup"><span data-stu-id="9cd77-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="9cd77-111">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="9cd77-112">Ayrıca, bir dizi yapıları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cd77-112">You can also declare an array of structures.</span></span> <span data-ttu-id="9cd77-113">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="9cd77-114">Bu veri mimarisine bileşenlerine erişmek için bu kuralların izleyin.</span><span class="sxs-lookup"><span data-stu-id="9cd77-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="9cd77-115">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="9cd77-116">Yapıları ve nesneler</span><span class="sxs-lookup"><span data-stu-id="9cd77-116">Structures and Objects</span></span>  
 <span data-ttu-id="9cd77-117">Bir yapının bir nesne bir veya daha fazla alt öğeleri olarak içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="9cd77-118">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="9cd77-119">Böyle bir bildirim belirli nesne sınıfı kullanmanız gereken yerine `Object`.</span><span class="sxs-lookup"><span data-stu-id="9cd77-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="9cd77-120">Yapılar ve yordamları</span><span class="sxs-lookup"><span data-stu-id="9cd77-120">Structures and Procedures</span></span>  
 <span data-ttu-id="9cd77-121">Bir yordam bağımsız değişkeni bir yapı geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cd77-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="9cd77-122">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="9cd77-123">Yukarıdaki örnekte yapısı geçirir *başvuruya göre*, yordamı çağıran kod değişiklikler etkili şekilde öğeleri değiştirin sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cd77-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="9cd77-124">Bir yapı bu tür değişiklik karşı korumak istiyorsanız, değere göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="9cd77-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="9cd77-125">Ayrıca bir yapısından döndürebilir bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="9cd77-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="9cd77-126">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="9cd77-127">Yapıları içindeki yapıları</span><span class="sxs-lookup"><span data-stu-id="9cd77-127">Structures Within Structures</span></span>  
 <span data-ttu-id="9cd77-128">Yapılar, diğer yapılar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-128">Structures can contain other structures.</span></span> <span data-ttu-id="9cd77-129">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="9cd77-130">Ayrıca, farklı bir modülde tanımlanmış bir yapı içinde bir modülde tanımlanmış bir yapı kapsüllemek için bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cd77-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="9cd77-131">Yapılar için rastgele bir derinlik diğer yapılar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9cd77-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd77-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cd77-132">See also</span></span>
- [<span data-ttu-id="9cd77-133">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9cd77-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="9cd77-134">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9cd77-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="9cd77-135">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9cd77-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="9cd77-136">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="9cd77-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="9cd77-137">Yapılar</span><span class="sxs-lookup"><span data-stu-id="9cd77-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="9cd77-138">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="9cd77-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="9cd77-139">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="9cd77-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="9cd77-140">Yapı Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9cd77-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="9cd77-141">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="9cd77-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="9cd77-142">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="9cd77-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
