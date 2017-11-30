---
title: "Nasıl yapılır: İmzasız arkadaş derlemeleri (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2b2667c60a07a2897a0934d210901042e2e43c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Nasıl yapılır: İmzasız arkadaş derlemeleri (Visual Basic) oluşturma
Bu örnek imzasız derlemeler ile arkadaş derlemeleri kullanmayı gösterir.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Bir derlemeyi hem bir derlemeyi oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Adlı bir Visual Basic dosyası oluşturma `friend_signed_A.` aşağıdaki kodu içerir. Kod kullanan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B Arkadaş derlemesi olarak bildirmek için öznitelik.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  Derleme ve friend_signed_A aşağıdaki komutu kullanarak oturum açın.  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  Adlı bir Visual Basic dosyası oluşturma `friend_unsigned_B` aşağıdaki kodu içerir. Friend_unsigned_A friend_unsigned_B arkadaş derleme olarak belirttiğinden friend_unsigned_B kodda erişebilirsiniz `Friend` türleri ve friend_unsigned_A üyelerinden.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  Aşağıdaki komutu kullanarak friend_signed_B derleyin.  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Derleyici tarafından üretilen derlemenin adını geçirilir arkadaş derleme adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Kullanarak açıkça derleme ayarlayabilirsiniz `/out` derleyici seçeneği.  
  
6.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     İki dizeyi program yazdırır: "Class1.Test" ve "Class2.Test".  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> kodu, belirli bir bölüme çalıştırmak için güvenlik izinleri ancak talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetler görünürlüğünü `Friend` türleri ve üyeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Arkadaş derlemeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Nasıl yapılır: imzalı arkadaş derlemeleri (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Programlama Kılavuzu kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
