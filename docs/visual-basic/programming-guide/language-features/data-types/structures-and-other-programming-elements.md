---
description: 'Daha fazla bilgi edinin: yapılar ve diğer programlama öğeleri (Visual Basic)'
title: Yapılar ve Diğer Programlama Öğeleri
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 62052389b617849566a3cd0c475a2eb5da9e61ca
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430592"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="55db4-103">Yapılar ve Diğer Programlama Öğeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55db4-103">Structures and Other Programming Elements (Visual Basic)</span></span>

<span data-ttu-id="55db4-104">Yapıları diziler, nesneler ve yordamlarla birlikte, birbirleriyle de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55db4-104">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="55db4-105">Etkileşimler, bu öğeler tek tek kullanıldığı için aynı sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="55db4-105">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55db4-106">Yapı bildiriminde yapı öğelerinden hiçbirini başlatamıyor.</span><span class="sxs-lookup"><span data-stu-id="55db4-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="55db4-107">Yalnızca bir yapı türü olarak tanımlanmış bir değişkenin öğelerine değerler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55db4-107">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="55db4-108">Yapılar ve diziler</span><span class="sxs-lookup"><span data-stu-id="55db4-108">Structures and Arrays</span></span>  

 <span data-ttu-id="55db4-109">Bir yapı, öğelerinden biri veya daha fazlası olarak bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="55db4-109">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="55db4-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-110">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="55db4-111">Bir yapı içindeki bir dizinin değerlerine, bir nesne üzerindeki bir özelliğe erişirken aynı şekilde erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55db4-111">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="55db4-112">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-112">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="55db4-113">Ayrıca, bir yapı dizisi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55db4-113">You can also declare an array of structures.</span></span> <span data-ttu-id="55db4-114">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-114">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="55db4-115">Bu veri mimarisinin bileşenlerine erişmek için aynı kurallara uyun.</span><span class="sxs-lookup"><span data-stu-id="55db4-115">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="55db4-116">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-116">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="55db4-117">Yapılar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="55db4-117">Structures and Objects</span></span>  

 <span data-ttu-id="55db4-118">Bir yapı, bir veya daha fazla öğelerinden oluşan bir nesne içerebilir.</span><span class="sxs-lookup"><span data-stu-id="55db4-118">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="55db4-119">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-119">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="55db4-120">Bu tür bir bildirimde, yerine belirli bir nesne sınıfını kullanmanız gerekir `Object` .</span><span class="sxs-lookup"><span data-stu-id="55db4-120">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="55db4-121">Yapılar ve yordamlar</span><span class="sxs-lookup"><span data-stu-id="55db4-121">Structures and Procedures</span></span>  

 <span data-ttu-id="55db4-122">Bir yapıyı yordam bağımsız değişkeni olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55db4-122">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="55db4-123">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-123">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="55db4-124">Önceki örnek, yapıyı *başvuruya göre* geçirir, bu da değişikliklerin çağıran kodda etkili olması için öğelerini değiştirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="55db4-124">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="55db4-125">Bir yapıyı bu değişikliğe karşı korumak istiyorsanız, değere göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="55db4-125">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="55db4-126">Ayrıca, bir yordamdan bir yapı da döndürebilirsiniz `Function` .</span><span class="sxs-lookup"><span data-stu-id="55db4-126">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="55db4-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-127">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="55db4-128">Yapılar Içindeki yapılar</span><span class="sxs-lookup"><span data-stu-id="55db4-128">Structures Within Structures</span></span>  

 <span data-ttu-id="55db4-129">Yapılar, diğer yapıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="55db4-129">Structures can contain other structures.</span></span> <span data-ttu-id="55db4-130">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55db4-130">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="55db4-131">Bu tekniği, farklı bir modülde tanımlanan bir yapıda bir modülde tanımlanan bir yapıyı kapsüllemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55db4-131">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="55db4-132">Yapılar, rastgele bir derinlikte diğer yapıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="55db4-132">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55db4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55db4-133">See also</span></span>

- [<span data-ttu-id="55db4-134">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="55db4-134">Data Types</span></span>](index.md)
- [<span data-ttu-id="55db4-135">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="55db4-135">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="55db4-136">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="55db4-136">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="55db4-137">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="55db4-137">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="55db4-138">Yapılar</span><span class="sxs-lookup"><span data-stu-id="55db4-138">Structures</span></span>](structures.md)
- [<span data-ttu-id="55db4-139">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="55db4-139">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="55db4-140">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="55db4-140">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="55db4-141">Yapı Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="55db4-141">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="55db4-142">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="55db4-142">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="55db4-143">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="55db4-143">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
