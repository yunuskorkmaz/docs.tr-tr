---
title: 'Nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma'
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
ms.openlocfilehash: 02acda34783afceaeb83d0d0752e5247747b5337
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667309"
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>Nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma
Bu örnek, arkadaş derlemeleri tanımlayıcı adlara sahip derlemeler ile kullanma işlemini gösterir. İki derleme tanımlayıcı ada gerekir. Bu örnekte iki derleme, aynı anahtarları kullanmak olsa da, anahtarları farklı iki derlemeler için kullanabilirsiniz.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>İmzalı bir derleme ve arkadaş derleme oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Aşağıdaki komut dizisi, tanımlayıcı ad aracı ile bir keyfile oluşturur ve ortak anahtarını görüntülemek için kullanın. Daha fazla bilgi için bkz. [Sn.exe (tanımlayıcı ad aracı)][Sn.exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
    1.  Bu örnek için bir tanımlayıcı ad anahtar oluşturun ve FriendAssemblies.snk dosyasında depolar:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  FriendAssemblies.snk ortak anahtarı ayıklar ve FriendAssemblies.publickey yerleştirin:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  FriendAssemblies.publickey dosyasında depolanan ortak anahtarı görüntüler:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Adlı bir Visual Basic dosyası oluşturma `friend_signed_A` , aşağıdaki kodu içerir. Kod <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B arkadaş derleme olarak bildirmek için özniteliği.  
  
     Tanımlayıcı ad aracı, her çalıştığında yeni bir ortak anahtar oluşturur. Bu nedenle, aşağıdaki örnekte gösterildiği gibi ürettiğiniz, ortak anahtar ile ortak anahtar aşağıdaki kodu değiştirmelisiniz.  
  
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
  
4.  Derleme ve aşağıdaki komutu kullanarak friend_signed_A imzalayın.  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  Adlı bir Visual Basic dosyası oluşturma `friend_signed_B` ve aşağıdaki kodu içerir. Friend_signed_A friend_signed_B arkadaş derleme olarak belirttiğinden friend_signed_B kodda erişip `Friend` türleri ve üyeleri friend_signed_A. Dosya, aşağıdaki kodu içerir.  
  
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
  
6.  Derleme ve aşağıdaki komutu kullanarak friend_signed_B imzalayın.  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     Geçirilen friend derleme adı derleyici tarafından oluşturulan bütünleştirilmiş kodun adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Bütünleştirilmiş kod kullanarak açıkça ayarlayabilirsiniz `-out` derleyici seçeneği. Daha fazla bilgi için [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     Program "Class1.Test" dizesini görüntüler.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> ise kod, belirli bir bölümünü çalıştırmak için güvenlik izinleri talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetimleri görünürlüğünü `Friend` türler ve üyeler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [Arkadaş derlemeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)
- [Nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [-keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md))
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
