---
title: 'Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19c301c6b96e1070447401af9105fba2e0f0837f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973364"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma
Bu örnek, friend derlemelerinin tanımlayıcı adlara sahip Derlemelerle nasıl kullanılacağını gösterir. Her iki derlemenin de tanımlayıcı adlandırılmış olması gerekir. Bu örnekteki her iki derleme de aynı anahtarları kullanmasına karşın, iki derleme için farklı anahtarlar kullanabilirsiniz.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>İmzalı derleme ve arkadaş derleme oluşturma  
  
1. Bir komut istemi açın.  
  
2. Anahtar oluşturma ve ortak anahtarını görüntüleme için tanımlayıcı ad aracı ile aşağıdaki komut dizisini kullanın. Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Bu örnek için bir tanımlayıcı ad anahtarı oluşturun ve *FriendAssemblies. snk*dosyasında depolayın:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Ortak anahtarı *FriendAssemblies. snk* konumundan ayıklayın ve *FriendAssemblies. PublicKey*dosyasına yerleştirin:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. *FriendAssemblies. PublicKey*dosyasında depolanan ortak anahtarı görüntüle:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Aşağıdaki kodu C# içeren *friend_signed_A* adlı bir veya Visual Basic dosya oluşturun. Kod, *friend_signed_B* bir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Friend derlemesi olarak bildirmek için özniteliğini kullanır.  
   
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
   
4. Aşağıdaki komutu kullanarak *friend_signed_A* derleyin ve imzalayın.  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. Aşağıdaki kodu C# içeren *friend_signed_B* adlı bir veya Visual Basic dosya oluşturun. *Friend_signed_A* , bir Friend derlemesi olarak *friend_signed_B* belirttiğinden, *friend_signed_B* içindeki kod, *friend_signed_A*'deki (C#) veya `Friend` (Visual Basic) türlerine veya üyelerine erişebilir `internal` . Dosya aşağıdaki kodu içerir.  
   
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
   
6. Aşağıdaki komutu kullanarak *friend_signed_B* derleyin ve imzalayın.  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   Derleyici tarafından oluşturulan derlemenin adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir. `/out` Derleyici seçeneğini kullanarak çıkış derlemesinin adını ( *. exe* veya *. dll*) açıkça belirtmeniz gerekir. Daha fazla bilgi için bkz. [/OutC# (derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).  
   
7. *Friend_signed_B. exe* dosyasını çalıştırın.  
   
   Program **Class1. test**dizesini çıktı.  
  
## <a name="net-security"></a>.NET güvenliği  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Özniteliği<xref:System.Security.Permissions.StrongNameIdentityPermission> ve sınıfı arasında benzerlikler vardır. Temel <xref:System.Security.Permissions.StrongNameIdentityPermission> fark, kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ancak `internal` öznitelik (C#) veya `Friend` (Visual Basic) türlerinin görünürlüğünü ve üyelerini denetler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Arkadaş derlemeleri](friend.md)
- [Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma](create-unsigned-friend.md)
- [/keyfile (C#)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn. exe (tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
- [C#Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
