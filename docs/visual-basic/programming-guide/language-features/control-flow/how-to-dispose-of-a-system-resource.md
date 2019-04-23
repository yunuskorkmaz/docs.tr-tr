---
title: 'Nasıl yapılır: (Visual Basic) bir sistem kaynağını atma'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: e3594db036edc3a6288b0373737c1ee26a691a57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341913"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir sistem kaynağını atma
Kullanabileceğiniz bir `Using` kodunuzun blok çıktığında sistemin bir kaynağın siler güvence altına almak için blok. Bu, büyük miktarda bellek tüketen veya diğer bileşenleri de kullanmak istediğiniz bir sistem kaynağını kullanıyorsanız yararlı olur.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Bir veritabanı bağlantı ile kodunuzu sona erdiğinde silmek için  
  
1. Uygun eklediğinizden emin olun [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kaynak dosyasının başında veritabanı bağlantısı için (Bu durumda, <xref:System.Data.SqlClient>).  
  
2. Oluşturma bir `Using` ile block `Using` ve `End Using` deyimleri. Veritabanı bağlantısı ile ilgilenen bir kod bloğunun içine yerleştirin.  
  
3. Bağlantı bildirme ve bir örneğini bir parçası olarak oluşturma `Using` deyimi.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     İşlenmeyen bir özel durumu içeren blok çıkış ne olursa olsun kaynak sistem siler.  
  
     Erişemiyorsanız Not `sqc` gelen dışında `Using` kapsamı blokla sınırlı olduğu için engelleyin.  
  
     Bir dosya tanıtıcısı veya COM sarmalayıcı gibi bir sistem kaynağına aynı tekniği kullanabilirsiniz. Kullandığınız bir `Using` block emin olmak için çıkılana sonra diğer bileşenleri için kullanılabilen kaynak bırakmak istediğinizde `Using` blok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient.SqlConnection>
- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Karar Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using Deyimi](../../../../visual-basic/language-reference/statements/using-statement.md)
