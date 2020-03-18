---
title: 'Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159500"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma
Bu örnek, güçlü adlara sahip derlemelerle arkadaş derlemelerinin nasıl kullanılacağını gösterir. Her iki derlemede de güçlü bir isim lendirilmelidir. Bu örnekteki her iki derleme de aynı anahtarları kullansa da, iki derleme için farklı anahtarlar kullanabilirsiniz.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>İmzalı derleme ve arkadaş derlemesi oluşturma  
  
1. Bir komut istemi açın.  
  
2. Bir anahtar dosyası oluşturmak ve ortak anahtarını görüntülemek için Güçlü Ad aracıyla aşağıdaki komut sırasını kullanın. Daha fazla bilgi için [Bkz. Sn.exe (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Bu örnek için güçlü bir ad anahtarı oluşturun ve *FriendAssemblies.snk*dosyasında saklayın:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. *FriendAssemblies.snk* gelen ortak anahtarı ayıklayın ve *FriendAssemblies.publickey*içine koymak:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. *FriendAssemblies.publickey*dosyasında depolanan ortak anahtarı görüntüleyin:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Aşağıdaki kodu içeren *friend_signed_A* adlı bir C# veya Visual Basic dosyası oluşturun. Kod, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *friend_signed_B* arkadaş derlemesi olarak bildirmek için özniteliği kullanır.  

   Güçlü Ad aracı her çalıştığında yeni bir ortak anahtar oluşturur. Bu nedenle, aşağıdaki koddaki ortak anahtarı, aşağıdaki örnekte gösterildiği gibi, oluşturduğunuz ortak anahtarla değiştirmeniz gerekir.  

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

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. Aşağıdaki komutu kullanarak *friend_signed_A* derve imzalayın.  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. Aşağıdaki kodu içeren *friend_signed_B* adlı bir C# veya Visual Basic dosyası oluşturun. *friend_signed_A* *friend_signed_B* bir arkadaş derlemesi olarak belirttiğinden, *friend_signed_B'daki* `Friend` kod (C#) veya (Visual Basic) türlerine ve *friend_signed_A'dan*üyelere erişebilir. `internal` Dosya aşağıdaki kodu içerir.  

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

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. Aşağıdaki komutu kullanarak *friend_signed_B* derleyip imzalayın.  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   Derleyici tarafından oluşturulan derlemenin adı öznitelik geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> arkadaş derleme adı eşleşmelidir. `-out` Derleyici seçeneğini kullanarak çıktı derlemesinin *(.exe* veya *.dll)* adını açıkça belirtmeniz gerekir. Daha fazla bilgi için bkz: [-out (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).  

7. *friend_signed_B.exe* dosyasını çalıştırın.  

   Program string **Class1.Test**çıktıları .  
  
## <a name="net-security"></a>.NET güvenlik  
 Öznitelik ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıf arasında benzerlikler vardır. Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> edebilirken, `internal` öznitelik (C#) veya (Visual Basic) türlerinin ve `Friend` üyelerinin görünürlüğünü denetler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Arkadaş meclisleri](friend.md)
- [Nasıl yapilir: İmzalanmamış arkadaş derlemeleri oluşturma](create-unsigned-friend.md)
- [-keyfile (C#)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
