---
title: 'Nasıl yapılır: İmzasız arkadaş derlemeleri (Visual Basic) oluşturma'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 873a5bf235b43b4460a1489a964539c4e4c18de3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643071"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Nasıl yapılır: İmzasız arkadaş derlemeleri (Visual Basic) oluşturma
Bu örnek imzasız derlemeler ile arkadaş derlemeleri kullanmayı gösterir.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Bir derlemeyi hem bir derlemeyi oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Adlı bir Visual Basic dosyası oluşturma `friend_signed_A.` aşağıdaki kodu içerir. Kod kullanan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B Arkadaş derlemesi olarak bildirmek için öznitelik.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
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
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Adlı bir Visual Basic dosyası oluşturma `friend_unsigned_B` aşağıdaki kodu içerir. Friend_unsigned_A friend_unsigned_B arkadaş derleme olarak belirttiğinden friend_unsigned_B kodda erişebilirsiniz `Friend` türleri ve friend_unsigned_A üyelerinden.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
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
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Derleyici tarafından üretilen derlemenin adını geçirilir arkadaş derleme adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Kullanarak açıkça derleme ayarlayabilirsiniz `/out` derleyici seçeneği.  
  
6.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     İki dizeyi program görüntüler: "Class1.Test" ve "Class2.Test".  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> kodu, belirli bir bölüme çalıştırmak için güvenlik izinleri ancak talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetler görünürlüğünü `Friend` türleri ve üyeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Arkadaş derlemeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Nasıl yapılır: imzalı arkadaş derlemeleri (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Programlama Kılavuzu kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
