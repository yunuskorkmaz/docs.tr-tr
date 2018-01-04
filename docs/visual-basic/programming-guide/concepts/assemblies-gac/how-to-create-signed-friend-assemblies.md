---
title: "Nasıl yapılır: imzalı arkadaş derlemeleri (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d3ffaf30cdcbc075b772a7350984d060e47fddb7
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>Nasıl yapılır: imzalı arkadaş derlemeleri (Visual Basic) oluşturma
Bu örnek güçlü adlara sahip Derlemelerle arkadaş derlemeleri kullanmayı gösterir. Her iki derlemeleri strong adlandırılmalıdır. Bu örnekte her iki derlemeleri aynı anahtarlar kullansa da, anahtarları farklı iki derlemeler için kullanabilirsiniz.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>İmzalı bir derleme ve bir derlemeyi oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Aşağıdaki komut dizisi tanımlayıcı ad aracı ile bir keyfile oluşturmak ve ortak anahtar görüntülemek için kullanın. Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)][Sn.exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
    1.  Bu örnek için bir tanımlayıcı ad anahtar oluştur ve FriendAssemblies.snk dosyada saklayabilir:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Ortak anahtar FriendAssemblies.snk ayıklayın ve FriendAssemblies.publickey koyun:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  FriendAssemblies.publickey dosyasında depolanan genel anahtarını görüntüleyin:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Adlı bir Visual Basic dosyası oluşturma `friend_signed_A` aşağıdaki kodu içerir. Kod kullanan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B Arkadaş derlemesi olarak bildirmek için öznitelik.  
  
     Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur. Bu nedenle, aşağıdaki örnekte gösterildiği gibi az önce oluşturulan, ortak anahtar ile aşağıdaki kodu ortak anahtar değiştirmelisiniz.  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  Derleme ve friend_signed_A aşağıdaki komutu kullanarak oturum açın.  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  Adlı bir Visual Basic dosyası oluşturma `friend_signed_B` ve aşağıdaki kodu içerir. Friend_signed_A friend_signed_B arkadaş derleme olarak belirttiğinden friend_signed_B kodda erişebilirsiniz `Friend` türleri ve friend_signed_A üyelerinden. Dosya şu kodu içerir.  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  Derleme ve friend_signed_B aşağıdaki komutu kullanarak oturum açın.  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     Derleyici tarafından üretilen derlemenin adını geçirilen arkadaş derleme adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Kullanarak açıkça derleme ayarlayabilirsiniz `/out` derleyici seçeneği. Daha fazla bilgi için bkz: [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     Program "Class1.Test" dizesi yazdırır.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> kodu, belirli bir bölüme çalıştırmak için güvenlik izinleri ancak talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetler görünürlüğünü `Friend` türleri ve üyeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Arkadaş derlemeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Nasıl yapılır: İmzasız arkadaş derlemeleri (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
