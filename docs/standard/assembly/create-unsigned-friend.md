---
title: 'Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: d8fdc3061067d85498dc5bbed7bf324f99169a36
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774342"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma

Bu örnekte, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Derleme ve arkadaş derleme oluşturma

1. Bir komut istemi açın.

2. Aşağıdaki kodu C# içeren *friend_unsigned_A* adlı bir veya Visual Basic dosya oluşturun. Kod, *friend_unsigned_B* bir Friend derlemesi olarak bildirmek için <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini kullanır.

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
   Imports System

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

4. Aşağıdaki kodu C# içeren *friend_unsigned_B* adlı bir veya Visual Basic dosya oluşturun. *Friend_unsigned_A* , bir Friend derlemesi olarak *Friend_unsigned_B* belirttiğinden, *friend_unsigned_B* içindeki kod `internal` (C#) veya`Friend`(Visual Basic) türlerine ve *friend_unsigned_A*' den üyelere erişebilir.

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

   Derleyici tarafından oluşturulan derlemenin adı, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğine geçirilen arkadaş derleme adı ile aynı olmalıdır. `-out` derleyici seçeneğini kullanarak çıkış derlemesinin ( *. exe* veya *. dll*) adını açıkça belirtmeniz gerekir. Daha fazla bilgi için bkz. [-OutC# (derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. *Friend_unsigned_B. exe* dosyasını çalıştırın.

   Program iki dizeyi çıktı: **Class1. test** ve **Class2. test**.

## <a name="net-security"></a>.NET güvenliği

@No__t_0 özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı arasında benzerlikler vardır. Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, ancak <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik `internal` veya `Friend` (Visual Basic) türlerinin ve üyelerinin görünürlüğünü denetler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Arkadaş derlemeleri](friend.md)
- [Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](create-signed-friend.md)
- [C#Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
