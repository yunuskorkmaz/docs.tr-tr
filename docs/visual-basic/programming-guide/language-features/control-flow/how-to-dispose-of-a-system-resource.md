---
title: 'Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)'
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
ms.openlocfilehash: c780ee1a174ad044593960bc30a3ee2e1f929390
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583140"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)
Kodunuzun bloğundan çıkılırken sistemin bir kaynağı ortadan kaldırabileceğini garantilemek için `Using` bloğu kullanabilirsiniz. Bu, büyük miktarda bellek tüketen bir sistem kaynağı kullanıyorsanız veya diğer bileşenlerin de kullanılmasını istiyorsanız kullanışlıdır.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Kodunuz ile işiniz bittiğinde bir veritabanı bağlantısını atmak için  
  
1. Kaynak dosyanızın başlangıcında (Bu durumda, <xref:System.Data.SqlClient>) veritabanı bağlantısı için uygun [Imports bildirisini (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) eklediğinizden emin olun.  
  
2. @No__t_1 ve `End Using` deyimleriyle `Using` bloğu oluşturun. Bloğun içinde, veritabanı bağlantısıyla ilgilenen kodu koyun.  
  
3. Bağlantıyı bildirin ve `Using` deyimin bir parçası olarak bir örneğini oluşturun.  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     İşlenmeyen bir özel durum da dahil olmak üzere bloğundan çıktığınızda sistem kaynağı ortadan kaldırsın.  
  
     Kapsamı bloğa sınırlı olduğundan, `Using` bloğunun dışından `sqc` erişemediğini unutmayın.  
  
     Bu tekniği, bir dosya tanıtıcısı veya bir COM sarmalayıcı gibi bir sistem kaynağı üzerinde kullanabilirsiniz. @No__t_1 bloğundan çıktıktan sonra kaynağın diğer bileşenler için kullanılabilir durumda kalmasını sağlamak istediğinizde bir `Using` bloğu kullanırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient.SqlConnection>
- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Karar Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using Deyimi](../../../../visual-basic/language-reference/statements/using-statement.md)
