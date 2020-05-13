---
title: 'Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma'
description: Bu makalede, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir. .NET güvenliği hakkındaki bilgileri içerir.
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 8d3e13669c36048759fedeb3df1bfb59fd476317
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378966"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="d732b-104">Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d732b-104">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="d732b-105">Bu örnekte, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d732b-105">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="d732b-106">Derleme ve arkadaş derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="d732b-106">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="d732b-107">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="d732b-107">Open a command prompt.</span></span>

2. <span data-ttu-id="d732b-108">Aşağıdaki kodu içeren *friend_unsigned_A* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d732b-108">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="d732b-109">Kod, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *friend_unsigned_B* bir Friend derlemesi olarak bildirmek için özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d732b-109">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="d732b-110">Aşağıdaki komutu kullanarak *friend_unsigned_A* derleyin ve imzalayın:</span><span class="sxs-lookup"><span data-stu-id="d732b-110">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="d732b-111">Aşağıdaki kodu içeren *friend_unsigned_B* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d732b-111">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="d732b-112">*Friend_unsigned_A* bir arkadaş derleme olarak *friend_unsigned_B* belirttiğinden *friend_unsigned_B* kodu, `internal` friend_unsigned_A Visual Basic (C#) veya `Friend` () türlerine ve üyelerine erişebilir. *friend_unsigned_A*</span><span class="sxs-lookup"><span data-stu-id="d732b-112">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="d732b-113">Aşağıdaki komutu kullanarak *friend_unsigned_B* derleyin.</span><span class="sxs-lookup"><span data-stu-id="d732b-113">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="d732b-114">Derleyici tarafından oluşturulan derlemenin adı, özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d732b-114">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="d732b-115">Derleyici seçeneğini kullanarak çıkış derlemesinin adını (*. exe* veya *. dll*) açıkça belirtmeniz gerekir `-out` .</span><span class="sxs-lookup"><span data-stu-id="d732b-115">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="d732b-116">Daha fazla bilgi için bkz. [-Out (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="d732b-116">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="d732b-117">*Friend_unsigned_B. exe* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d732b-117">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="d732b-118">Program iki dizeyi çıktı: **Class1. test** ve **Class2. test**.</span><span class="sxs-lookup"><span data-stu-id="d732b-118">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="d732b-119">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="d732b-119">.NET security</span></span>

<span data-ttu-id="d732b-120">Özniteliği ve sınıfı arasında benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> <xref:System.Security.Permissions.StrongNameIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="d732b-120">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="d732b-121">Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, ancak <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik `internal` veya `Friend` (Visual Basic) türlerinin görünürlüğünü ve üyelerini denetler.</span><span class="sxs-lookup"><span data-stu-id="d732b-121">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="d732b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d732b-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="d732b-123">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="d732b-123">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="d732b-124">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="d732b-124">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="d732b-125">Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d732b-125">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="d732b-126">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d732b-126">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d732b-127">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d732b-127">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
