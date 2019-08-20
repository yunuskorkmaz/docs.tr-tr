---
title: 'Nasıl yapılır: Imzalı arkadaş derlemeleri oluşturma (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 7715726a200150b044fb8e97216fa02d0e784838
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595933"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Nasıl yapılır: Imzalı arkadaş derlemeleri oluşturma (C#)
Bu örnek, friend derlemelerinin tanımlayıcı adlara sahip Derlemelerle nasıl kullanılacağını gösterir. Her iki derlemenin de tanımlayıcı adlandırılmış olması gerekir. Bu örnekteki her iki derleme de aynı anahtarları kullanmasına karşın, iki derleme için farklı anahtarlar kullanabilirsiniz.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>İmzalı derleme ve arkadaş derleme oluşturmak için  
  
1. Bir komut istemi açın.  
  
2. Anahtar oluşturma ve ortak anahtarını görüntüleme için tanımlayıcı ad aracı ile aşağıdaki komut dizisini kullanın. Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Bu örnek için bir tanımlayıcı ad anahtarı oluşturun ve FriendAssemblies. snk dosyasında depolayın:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Ortak anahtarı FriendAssemblies. snk konumundan ayıklayın ve FriendAssemblies. PublicKey dosyasına yerleştirin:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. FriendAssemblies. publickey dosyasında depolanan ortak anahtarı görüntüle:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Aşağıdaki kodu C# içeren adlı `friend_signed_A` bir dosya oluşturun. Kod, friend_signed_B bir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Friend derlemesi olarak bildirmek için özniteliğini kullanır.  
  
     Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur. Bu nedenle, aşağıdaki örnekte gösterildiği gibi aşağıdaki koddaki ortak anahtarı yeni oluşturduğunuz ortak anahtarla değiştirmelisiniz.  
  
    ```csharp  
    // friend_signed_A.cs  
    // Compile with:   
    // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    using System.Runtime.CompilerServices;  
  
    [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
    class Class1  
    {  
        public void Test()  
        {  
            System.Console.WriteLine("Class1.Test");  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
4. Aşağıdaki komutu kullanarak friend_signed_A derleyin ve imzalayın.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5. Adlı`friend_signed_B` bir C# dosya oluşturun ve aşağıdaki kodu içerir. Friend_signed_A, bir Friend derlemesi olarak friend_signed_B belirttiğinden, friend_signed_B içindeki kod friend_signed_A 'deki türlere `internal` ve üyelere erişebilir. Dosya aşağıdaki kodu içerir.  
  
    ```csharp  
    // friend_signed_B.cs  
    // Compile with:   
    // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            Class1 inst = new Class1();  
            inst.Test();  
        }  
    }  
    ```  
  
6. Aşağıdaki komutu kullanarak friend_signed_B derleyin ve imzalayın.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Derleyici tarafından oluşturulan derlemenin adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir. `/out` Derleyici seçeneğini kullanarak çıkış derlemesinin adını (. exe veya. dll) açıkça belirtmeniz gerekir.  Daha fazla bilgi için bkz. [/OutC# (derleyici seçenekleri)](../../../language-reference/compiler-options/out-compiler-option.md).  
  
7. Friend_signed_B. exe dosyasını çalıştırın.  
  
     Program, "Class1. test" dizesini yazdırır.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Özniteliği<xref:System.Security.Permissions.StrongNameIdentityPermission> ve sınıfı arasında benzerlikler vardır. Temel fark <xref:System.Security.Permissions.StrongNameIdentityPermission> , kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ancak `internal` öznitelik türlerin ve üyelerin görünürlüğünü denetler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../../standard/assembly/friend-assemblies.md)
- [Nasıl yapılır: Imzasız arkadaş derlemeleri oluşturma (C#)](./how-to-create-unsigned-friend-assemblies.md)
- [/keyfile](../../../language-reference/compiler-options/keyfile-compiler-option.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [C# Programlama Kılavuzu](../../index.md)
