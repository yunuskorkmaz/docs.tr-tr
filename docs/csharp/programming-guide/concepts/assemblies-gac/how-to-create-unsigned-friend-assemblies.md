---
title: 'Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)'
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 6bc2d807b3d1cf6c82a9ba6303139b9758581f35
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318240"
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)
Bu örnek, işaretsiz derlemeleri ile arkadaş derlemeleri kullanmayı gösterir.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Bir derleme ve arkadaş derleme oluşturmak için  
  
1. Bir komut istemi açın.  
  
2. Adlı bir C# dosyası oluşturma `friend_unsigned_A.` , aşağıdaki kodu içerir. Kod <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_unsigned_B arkadaş derleme olarak bildirmek için özniteliği.  
  
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
  
3. Derleme ve aşağıdaki komutu kullanarak friend_unsigned_A imzalayın.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4. Adlı bir C# dosyası oluşturma `friend_unsigned_B` , aşağıdaki kodu içerir. Friend_unsigned_A friend_unsigned_B arkadaş derleme olarak belirttiğinden friend_unsigned_B kodda erişip `internal` türleri ve üyeleri friend_unsigned_A.  
  
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
  
5. Aşağıdaki komutu kullanarak friend_unsigned_B derleyin.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     Geçirilen friend derleme adı derleyici tarafından oluşturulan bütünleştirilmiş kodun adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Çıktı derlemesine (.exe veya .dll) adını kullanarak açıkça belirtmeniz gerekir `/out` derleyici seçeneği. Daha fazla bilgi için [/out (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
6. Friend_unsigned_B.exe dosyasını çalıştırın.  
  
     Program iki dizeyi yazdırır: "Class1.Test" ve "Class2.Test".  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> ise kod, belirli bir bölümünü çalıştırmak için güvenlik izinleri talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetimleri görünürlüğünü `internal` türler ve üyeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../../standard/assembly/friend-assemblies.md)
- [Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
