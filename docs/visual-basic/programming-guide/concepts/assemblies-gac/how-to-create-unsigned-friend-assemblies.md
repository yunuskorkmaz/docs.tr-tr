---
title: 'Nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
ms.openlocfilehash: 814c2584ea9e1e14c3af003a0515166f53b6d913
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819391"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma
Bu örnek, işaretsiz derlemeleri ile arkadaş derlemeleri kullanmayı gösterir.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Bir derleme ve arkadaş derleme oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  Adlı bir Visual Basic dosyası oluşturma `friend_signed_A.` , aşağıdaki kodu içerir. Kod <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B arkadaş derleme olarak bildirmek için özniteliği.  
  
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
  
3.  Derleme ve aşağıdaki komutu kullanarak friend_signed_A imzalayın.  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Adlı bir Visual Basic dosyası oluşturma `friend_unsigned_B` , aşağıdaki kodu içerir. Friend_unsigned_A friend_unsigned_B arkadaş derleme olarak belirttiğinden friend_unsigned_B kodda erişip `Friend` türleri ve üyeleri friend_unsigned_A.  
  
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
  
     Geçirilen friend derleme adı derleyici tarafından oluşturulan bütünleştirilmiş kodun adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Bütünleştirilmiş kod kullanarak açıkça ayarlayabilirsiniz `/out` derleyici seçeneği.  
  
6.  Friend_signed_B.exe dosyasını çalıştırın.  
  
     Program iki dizeyi görüntüler: "Class1.Test" ve "Class2.Test".  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı. Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> ise kod, belirli bir bölümünü çalıştırmak için güvenlik izinleri talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetimleri görünürlüğünü `Friend` türler ve üyeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../../standard/assembly/friend-assemblies.md)
- [Nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Programlama Kılavuzu kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
