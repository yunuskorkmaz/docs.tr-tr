---
title: (Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 860c41e73aa2d45ca1a9adcb3031834545e2fb37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642694"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="56a90-102">(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="56a90-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>
<span data-ttu-id="56a90-103">Eşdeğişken arabirimi arabiriminde belirtilenlerden daha türetilmiş türler döndürülecek yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="56a90-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="56a90-104">Karşıtı arabirimi belirtilenlerden daha az türetilmiş türler arabiriminde parametrelerinin kabul etmek yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="56a90-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="56a90-105">.NET Framework 4'te birkaç varolan arabirimleri eşdeğişken hale geldi ve karşıtı.</span><span class="sxs-lookup"><span data-stu-id="56a90-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="56a90-106">Bunlar <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="56a90-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="56a90-107">Genel koleksiyonlar türetilen türler için temel türleri çalışır yöntemleri yeniden kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="56a90-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="56a90-108">.NET Framework'teki değişken arabirimler listesi için bkz: [genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="56a90-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="56a90-109">Genel koleksiyonlar dönüştürme</span><span class="sxs-lookup"><span data-stu-id="56a90-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="56a90-110">Aşağıdaki örnek Kovaryans desteği yararları gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="56a90-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="56a90-111">`PrintFullName` Yöntemi kabul koleksiyonu `IEnumerable(Of Person)` türünü bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="56a90-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="56a90-112">Ancak, onu bir koleksiyonu için tekrar kullanabilirsiniz `IEnumerable(Of Person)` yazın, çünkü `Employee` devralır `Person`.</span><span class="sxs-lookup"><span data-stu-id="56a90-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarchy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
' The method has a parameter of the IEnumerable(Of Person) type.  
Public Sub PrintFullName(ByVal persons As IEnumerable(Of Person))  
    For Each person As Person In persons  
        Console.WriteLine(  
            "Name: " & person.FirstName & " " & person.LastName)  
    Next  
End Sub  
  
Sub Main()  
    Dim employees As IEnumerable(Of Employee) = New List(Of Employee)  
  
    ' You can pass IEnumerable(Of Employee),   
    ' although the method expects IEnumerable(Of Person).  
  
    PrintFullName(employees)  
  
End Sub  
```  
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="56a90-113">Genel koleksiyonları karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="56a90-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="56a90-114">Aşağıdaki örnekte, değişken karşıtı desteği yararları gösterilmektedir <xref:System.Collections.Generic.IComparer%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="56a90-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="56a90-115">`PersonComparer` Uygulayan sınıf `IComparer(Of Person)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="56a90-115">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="56a90-116">Ancak, bir dizi nesnelerin karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz `Employee` yazın, çünkü `Employee` devralır `Person`.</span><span class="sxs-lookup"><span data-stu-id="56a90-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarhcy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
' The custom comparer for the Person type  
' with standard implementations of Equals()  
' and GetHashCode() methods.  
Class PersonComparer  
    Implements IEqualityComparer(Of Person)  
  
    Public Function Equals1(  
        ByVal x As Person,  
        ByVal y As Person) As Boolean _  
        Implements IEqualityComparer(Of Person).Equals  
  
        If x Is y Then Return True  
        If x Is Nothing OrElse y Is Nothing Then Return False  
        Return (x.FirstName = y.FirstName) AndAlso  
            (x.LastName = y.LastName)  
    End Function  
    Public Function GetHashCode1(  
        ByVal person As Person) As Integer _  
        Implements IEqualityComparer(Of Person).GetHashCode  
  
        If person Is Nothing Then Return 0  
        Dim hashFirstName =  
            If(person.FirstName Is Nothing,  
            0, person.FirstName.GetHashCode())  
        Dim hashLastName = person.LastName.GetHashCode()  
        Return hashFirstName Xor hashLastName  
    End Function  
End Class  
  
Sub Main()  
    Dim employees = New List(Of Employee) From {  
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},  
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}  
    }  
  
    ' You can pass PersonComparer,   
    ' which implements IEqualityComparer(Of Person),  
    ' although the method expects IEqualityComparer(Of Employee)  
  
    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())  
  
    For Each employee In noduplicates  
        Console.WriteLine(employee.FirstName & " " & employee.LastName)  
    Next  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="56a90-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56a90-117">See Also</span></span>  
 [<span data-ttu-id="56a90-118">Genel arabirimler (Visual Basic) varyans</span><span class="sxs-lookup"><span data-stu-id="56a90-118">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
