---
title: "Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 854df39394ef10bf2404fb3f762586fb102fba7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma
Bu örnek imzasız derlemeler ile arkadaş derlemeleri kullanmayı gösterir.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Bir derlemeyi hem bir derlemeyi oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Adlı bir C# dosyası oluşturun `friend_signed_A.` aşağıdaki kodu içerir. Kod kullanan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B Arkadaş derlemesi olarak bildirmek için öznitelik.  
  
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
  
3.  Derleme ve friend_signed_A aşağıdaki komutu kullanarak oturum açın.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  Adlı bir C# dosyası oluşturun `friend_unsigned_B` aşağıdaki kodu içerir. Friend_unsigned_A friend_unsigned_B arkadaş derleme olarak belirttiğinden friend_unsigned_B kodda erişebilirsiniz `internal` türleri ve friend_unsigned_A üyelerinden.  
  
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
  
5.  Aşağıdaki komutu kullanarak friend_signed_B derleyin.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     Derleyici tarafından üretilen derlemenin adını geçirilir arkadaş derleme adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Çıkış derlemesi (.exe veya .dll) adını kullanarak açıkça belirtmeniz gerekir `/out` derleyici seçeneği. Daha fazla bilgi için bkz: [/out (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
6.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     İki dizeyi program yazdırır: "Class1.Test" ve "Class2.Test".  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> kodu, belirli bir bölüme çalıştırmak için güvenlik izinleri ancak talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetler görünürlüğünü `internal` türleri ve üyeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Arkadaş derlemeler (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)
