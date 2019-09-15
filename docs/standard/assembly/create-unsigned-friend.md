---
title: 'Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9d5699f772dba994b10408d15422faa3c5931f45
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991692"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma

Bu örnekte, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Derleme ve arkadaş derleme oluşturma

1. Bir komut istemi açın.

2. Aşağıdaki kodu C# içeren *friend_unsigned_A* adlı bir veya Visual Basic dosya oluşturun. Kod, *friend_unsigned_B* bir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Friend derlemesi olarak bildirmek için özniteliğini kullanır.

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

4. Aşağıdaki kodu C# içeren *friend_unsigned_B* adlı bir veya Visual Basic dosya oluşturun. *Friend_unsigned_A* , bir Friend derlemesi olarak *friend_unsigned_B* belirttiğinden, *friend_unsigned_B* içindeki kod, friend_unsigned_A 'deki `internal` (C#) veya `Friend` (Visual Basic) türlerine veya üyelerine erişebilir.

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

   Derleyici tarafından oluşturulan derlemenin adı, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir. `/out` Derleyici seçeneğini kullanarak çıkış derlemesinin adını ( *. exe* veya *. dll*) açıkça belirtmeniz gerekir. Daha fazla bilgi için bkz. [/OutC# (derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. *Friend_unsigned_B. exe* dosyasını çalıştırın.

   Program iki dize çıktısı verir: **Class1. test** ve **Class2. test**.

## <a name="net-security"></a>.NET güvenliği

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Özniteliği<xref:System.Security.Permissions.StrongNameIdentityPermission> ve sınıfı arasında benzerlikler vardır. Temel fark <xref:System.Security.Permissions.StrongNameIdentityPermission> , kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ancak `internal` öznitelik veya `Friend` (Visual Basic) türlerinin görünürlüğünü ve üyelerini denetler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Arkadaş derlemeleri](friend.md)
- [Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma](create-signed-friend.md)
- [C#Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
