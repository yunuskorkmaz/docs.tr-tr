---
title: 'Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma'
description: Bu makalede, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir. .NET güvenliği hakkındaki bilgileri içerir.
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 69a696d7b4f940dc8ace2ab032c16107bb6df450
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480872"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma

Bu örnekte, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Derleme ve arkadaş derleme oluşturma

1. Bir komut istemi açın.

2. Aşağıdaki kodu içeren *friend_unsigned_A* adlı bir C# veya Visual Basic dosyası oluşturun. Kod, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *friend_unsigned_B* bir Friend derlemesi olarak bildirmek için özniteliğini kullanır.

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

3. Aşağıdaki komutu kullanarak *friend_unsigned_A* derleyin ve imzalayın:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Aşağıdaki kodu içeren *friend_unsigned_B* adlı bir C# veya Visual Basic dosyası oluşturun. *Friend_unsigned_A* bir arkadaş derleme olarak *friend_unsigned_B* belirttiğinden *friend_unsigned_B* kodu, `internal` friend_unsigned_A Visual Basic (C#) veya `Friend` () türlerine ve üyelerine erişebilir. 

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

5. Aşağıdaki komutu kullanarak *friend_unsigned_B* derleyin.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Derleyici tarafından oluşturulan derlemenin adı, özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> . Derleyici seçeneğini kullanarak çıkış derlemesinin adını (*. exe* veya *. dll*) açıkça belirtmeniz gerekir `-out` . Daha fazla bilgi için bkz. [ **OutputAssembly** (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/output.md#outputassembly) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. *friend_unsigned_B.exe* dosyasını çalıştırın.

   Program iki dizeyi çıktı: **Class1. test** ve **Class2. test**.

## <a name="net-security"></a>.NET güvenliği

Özniteliği ve sınıfı arasında benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> <xref:System.Security.Permissions.StrongNameIdentityPermission> . Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, ancak <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik `internal`  veya `Friend` (Visual Basic) türlerinin görünürlüğünü ve üyelerini denetler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Arkadaş derlemeleri](friend.md)
- [Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](create-signed-friend.md)
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
