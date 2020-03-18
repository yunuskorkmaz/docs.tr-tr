---
title: 'Nasıl yapilir: İmzalanmamış arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352431"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="9360f-102">Nasıl yapilir: İmzalanmamış arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="9360f-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="9360f-103">Bu örnek, imzalanmamış derlemelerle arkadaş derlemelerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9360f-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="9360f-104">Derleme ve arkadaş derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9360f-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="9360f-105">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="9360f-105">Open a command prompt.</span></span>

2. <span data-ttu-id="9360f-106">Aşağıdaki kodu içeren *friend_unsigned_A* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9360f-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="9360f-107">Kod, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *friend_unsigned_B* arkadaş derlemesi olarak bildirmek için özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="9360f-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

   ```csharp
   // friend_unsigned_A.cs
   // Compile with:
   // csc /target:library friend_unsigned_A.cs
   using System.Runtime.CompilerServices;
   using System;

   [assembly: InternalsVisibleTo("friend_unsigned_B")]

   // Type is internal by default.
   class Class1
   {
       public void Test()
       {
           Console.WriteLine("Class1.Test");
       }
   }

   // Public type with internal member.
   public class Class2
   {
       internal void Test()
       {
           Console.WriteLine("Class2.Test");
       }
   }
   ```

   ```vb
   ' friend_unsigned_A.vb
   ' Compile with:
   ' vbc -target:library friend_unsigned_A.vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("friend_unsigned_B")>

   ' Friend type.
   Friend Class Class1
       Public Sub Test()
           Console.WriteLine("Class1.Test")
       End Sub
   End Class

   ' Public type with Friend member.
   Public Class Class2
       Friend Sub Test()
           Console.WriteLine("Class2.Test")
       End Sub
   End Class
   ```

3. <span data-ttu-id="9360f-108">Aşağıdaki komutu kullanarak *friend_unsigned_A* derve imzalayın:</span><span class="sxs-lookup"><span data-stu-id="9360f-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="9360f-109">Aşağıdaki kodu içeren *friend_unsigned_B* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9360f-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="9360f-110">*friend_unsigned_A* *friend_unsigned_B* bir arkadaş derlemesi olarak belirttiğinden, *friend_unsigned_B'daki* `Friend` kod (C#) veya (Visual Basic) *türlerine*ve friend_unsigned_A'dan üyelere erişebilir. `internal`</span><span class="sxs-lookup"><span data-stu-id="9360f-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

   ```csharp
   // friend_unsigned_B.cs
   // Compile with:
   // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   public class Program
   {
       static void Main()
       {
           // Access an internal type.
           Class1 inst1 = new Class1();
           inst1.Test();

           Class2 inst2 = new Class2();
           // Access an internal member of a public type.
           inst2.Test();

           System.Console.ReadLine();
       }
   }
   ```

   ```vb
   ' friend_unsigned_B.vb
   ' Compile with:
   ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   Module Module1
       Sub Main()
           ' Access a Friend type.
           Dim inst1 As New Class1()
           inst1.Test()

           Dim inst2 As New Class2()
           ' Access a Friend member of a public type.
           inst2.Test()

           System.Console.ReadLine()
       End Sub
   End Module
   ```

5. <span data-ttu-id="9360f-111">Aşağıdaki komutu kullanarak *friend_unsigned_B* derle.</span><span class="sxs-lookup"><span data-stu-id="9360f-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="9360f-112">Derleyici tarafından oluşturulan derlemenin adı öznitelik geçirilir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> arkadaş derleme adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="9360f-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="9360f-113">`-out` Derleyici seçeneğini kullanarak çıktı derlemesinin *(.exe* veya *.dll)* adını açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9360f-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="9360f-114">Daha fazla bilgi için [bkz:out (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="9360f-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="9360f-115">*friend_unsigned_B.exe* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9360f-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="9360f-116">Program iki dize çıkar: **Class1.Test** ve **Class2.Test**.</span><span class="sxs-lookup"><span data-stu-id="9360f-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="9360f-117">.NET güvenlik</span><span class="sxs-lookup"><span data-stu-id="9360f-117">.NET security</span></span>

<span data-ttu-id="9360f-118">Öznitelik ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıf arasında benzerlikler vardır.</span><span class="sxs-lookup"><span data-stu-id="9360f-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="9360f-119">Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilirken, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `Friend` öznitelik veya (Visual Basic) türlerinin `internal` ve üyelerinin görünürlüğünü denetler.</span><span class="sxs-lookup"><span data-stu-id="9360f-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="9360f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9360f-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="9360f-121">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="9360f-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="9360f-122">Arkadaş meclisleri</span><span class="sxs-lookup"><span data-stu-id="9360f-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="9360f-123">Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="9360f-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="9360f-124">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9360f-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9360f-125">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9360f-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
