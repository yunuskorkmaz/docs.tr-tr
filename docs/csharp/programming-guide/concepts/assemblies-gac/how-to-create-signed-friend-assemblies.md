---
title: 'Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 13b99cd1118071e7c403828260003c80b9417792
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354498"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma (C#)
Bu örnek, arkadaş derlemeleri tanımlayıcı adlara sahip derlemeler ile kullanma işlemini gösterir. İki derleme tanımlayıcı ada gerekir. Bu örnekte iki derleme, aynı anahtarları kullanmak olsa da, anahtarları farklı iki derlemeler için kullanabilirsiniz.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>İmzalı bir derleme ve arkadaş derleme oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Aşağıdaki komut dizisi, tanımlayıcı ad aracı ile bir keyfile oluşturur ve ortak anahtarını görüntülemek için kullanın. Daha fazla bilgi için [Sn.exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1.  Bu örnek için bir tanımlayıcı ad anahtar oluşturun ve FriendAssemblies.snk dosyasında depolar:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  FriendAssemblies.snk ortak anahtarı ayıklar ve FriendAssemblies.publickey yerleştirin:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  FriendAssemblies.publickey dosyasında depolanan ortak anahtarı görüntüler:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Adlı bir C# dosyası oluşturma `friend_signed_A` , aşağıdaki kodu içerir. Kod <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B arkadaş derleme olarak bildirmek için özniteliği.  
  
     Tanımlayıcı ad aracı, her çalıştığında yeni bir ortak anahtar oluşturur. Bu nedenle, aşağıdaki örnekte gösterildiği gibi ürettiğiniz, ortak anahtar ile ortak anahtar aşağıdaki kodu değiştirmelisiniz.  
  
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
  
4.  Derleme ve aşağıdaki komutu kullanarak friend_signed_A imzalayın.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  Adlı bir C# dosyası oluşturma `friend_signed_B` ve aşağıdaki kodu içerir. Friend_signed_A friend_signed_B arkadaş derleme olarak belirttiğinden friend_signed_B kodda erişip `internal` türleri ve üyeleri friend_signed_A. Dosya, aşağıdaki kodu içerir.  
  
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
  
6.  Derleme ve aşağıdaki komutu kullanarak friend_signed_B imzalayın.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Geçirilen friend derleme adı derleyici tarafından oluşturulan bütünleştirilmiş kodun adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Çıktı derlemesine (.exe veya .dll) adını kullanarak açıkça belirtmeniz gerekir `/out` derleyici seçeneği.  Daha fazla bilgi için [/out (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
7.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     Program "Class1.Test" dize yazdırır.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> ise kod, belirli bir bölümünü çalıştırmak için güvenlik izinleri talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetimleri görünürlüğünü `internal` türler ve üyeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../../standard/assembly/friend-assemblies.md)
- [Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [/keyfile](../../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
