---
title: 'Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 34243a65f57f41c358439baac82a1ce169233259
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma
Bu örnek güçlü adlara sahip Derlemelerle arkadaş derlemeleri kullanmayı gösterir. Her iki derlemeleri strong adlandırılmalıdır. Bu örnekte her iki derlemeleri aynı anahtarlar kullansa da, anahtarları farklı iki derlemeler için kullanabilirsiniz.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>İmzalı bir derleme ve bir derlemeyi oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Aşağıdaki komut dizisi tanımlayıcı ad aracı ile bir keyfile oluşturmak ve ortak anahtar görüntülemek için kullanın. Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23).  
  
    1.  Bu örnek için bir tanımlayıcı ad anahtar oluştur ve FriendAssemblies.snk dosyada saklayabilir:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Ortak anahtar FriendAssemblies.snk ayıklayın ve FriendAssemblies.publickey koyun:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  FriendAssemblies.publickey dosyasında depolanan genel anahtarını görüntüleyin:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Adlı bir C# dosyası oluşturun `friend_signed_A` aşağıdaki kodu içerir. Kod kullanan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B Arkadaş derlemesi olarak bildirmek için öznitelik.  
  
     Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur. Bu nedenle, aşağıdaki örnekte gösterildiği gibi az önce oluşturulan, ortak anahtar ile aşağıdaki kodu ortak anahtar değiştirmelisiniz.  
  
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
  
4.  Derleme ve friend_signed_A aşağıdaki komutu kullanarak oturum açın.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  Adlı bir C# dosyası oluşturma `friend_signed_B` ve aşağıdaki kodu içerir. Friend_signed_A friend_signed_B arkadaş derleme olarak belirttiğinden friend_signed_B kodda erişebilirsiniz `internal` türleri ve friend_signed_A üyelerinden. Dosya şu kodu içerir.  
  
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
  
6.  Derleme ve friend_signed_B aşağıdaki komutu kullanarak oturum açın.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Derleyici tarafından üretilen derlemenin adını geçirilen arkadaş derleme adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Çıkış derlemesi (.exe veya .dll) adını kullanarak açıkça belirtmeniz gerekir `/out` derleyici seçeneği.  Daha fazla bilgi için bkz: [/out (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
7.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     Program "Class1.Test" dizesi yazdırır.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> kodu, belirli bir bölüme çalıştırmak için güvenlik izinleri ancak talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetler görünürlüğünü `internal` türleri ve üyeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Arkadaş derlemeler (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Sn.exe (Tanımlayıcı Ad Aracı)](https://msdn.microsoft.com/library/k5b5tt23)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
