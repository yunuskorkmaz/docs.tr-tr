---
title: 'Nasıl yapılır: Imzasız arkadaş derlemeleri oluşturma (C#)'
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 5dadd725234048c4b6a4f9a0fa9b38dbf92671aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595916"
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Nasıl yapılır: Imzasız arkadaş derlemeleri oluşturma (C#)
Bu örnekte, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Derleme ve arkadaş derleme oluşturmak için  
  
1. Bir komut istemi açın.  
  
2. Aşağıdaki kodu C# içeren adlı `friend_unsigned_A.` bir dosya oluşturun. Kod, friend_unsigned_B bir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Friend derlemesi olarak bildirmek için özniteliğini kullanır.  
  
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
  
3. Aşağıdaki komutu kullanarak friend_unsigned_A derleyin ve imzalayın.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4. Aşağıdaki kodu C# içeren adlı `friend_unsigned_B` bir dosya oluşturun. Friend_unsigned_A, bir Friend derlemesi olarak friend_unsigned_B belirttiğinden, friend_unsigned_B içindeki kod friend_unsigned_A 'deki türlere `internal` ve üyelere erişebilir.  
  
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
  
     Derleyici tarafından oluşturulan derlemenin adı, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir. `/out` Derleyici seçeneğini kullanarak çıkış derlemesinin adını (. exe veya. dll) açıkça belirtmeniz gerekir. Daha fazla bilgi için bkz. [/OutC# (derleyici seçenekleri)](../../../language-reference/compiler-options/out-compiler-option.md).  
  
6. Friend_unsigned_B. exe dosyasını çalıştırın.  
  
     Program iki dize yazdırır: "Class1. test" ve "Class2. test".  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Özniteliği<xref:System.Security.Permissions.StrongNameIdentityPermission> ve sınıfı arasında benzerlikler vardır. Temel fark <xref:System.Security.Permissions.StrongNameIdentityPermission> , kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ancak `internal` öznitelik türlerin ve üyelerin görünürlüğünü denetler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../../standard/assembly/friend-assemblies.md)
- [Nasıl yapılır: Imzalı arkadaş derlemeleri oluşturma (C#)](./how-to-create-signed-friend-assemblies.md)
- [C# Programlama Kılavuzu](../../index.md)
