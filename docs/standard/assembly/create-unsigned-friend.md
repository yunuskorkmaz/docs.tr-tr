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
# <a name="how-to-create-unsigned-friend-assemblies"></a>Nasıl yapilir: İmzalanmamış arkadaş derlemeleri oluşturma

Bu örnek, imzalanmamış derlemelerle arkadaş derlemelerinin nasıl kullanılacağını gösterir.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Derleme ve arkadaş derlemesi oluşturma

1. Bir komut istemi açın.

2. Aşağıdaki kodu içeren *friend_unsigned_A* adlı bir C# veya Visual Basic dosyası oluşturun. Kod, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *friend_unsigned_B* arkadaş derlemesi olarak bildirmek için özniteliği kullanır.

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

3. Aşağıdaki komutu kullanarak *friend_unsigned_A* derve imzalayın:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Aşağıdaki kodu içeren *friend_unsigned_B* adlı bir C# veya Visual Basic dosyası oluşturun. *friend_unsigned_A* *friend_unsigned_B* bir arkadaş derlemesi olarak belirttiğinden, *friend_unsigned_B'daki* `Friend` kod (C#) veya (Visual Basic) *türlerine*ve friend_unsigned_A'dan üyelere erişebilir. `internal`

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

5. Aşağıdaki komutu kullanarak *friend_unsigned_B* derle.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Derleyici tarafından oluşturulan derlemenin adı öznitelik geçirilir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> arkadaş derleme adı eşleşmelidir. `-out` Derleyici seçeneğini kullanarak çıktı derlemesinin *(.exe* veya *.dll)* adını açıkça belirtmeniz gerekir. Daha fazla bilgi için [bkz:out (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. *friend_unsigned_B.exe* dosyasını çalıştırın.

   Program iki dize çıkar: **Class1.Test** ve **Class2.Test**.

## <a name="net-security"></a>.NET güvenlik

Öznitelik ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıf arasında benzerlikler vardır. Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilirken, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `Friend` öznitelik veya (Visual Basic) türlerinin `internal` ve üyelerinin görünürlüğünü denetler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Arkadaş meclisleri](friend.md)
- [Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma](create-signed-friend.md)
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
