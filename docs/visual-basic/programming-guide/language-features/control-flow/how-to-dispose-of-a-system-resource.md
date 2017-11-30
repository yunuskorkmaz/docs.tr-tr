---
title: "Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5b5c65c9d123c6f481852eb249cb4d479a180c5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)
Kullanabileceğiniz bir `Using` kodunuzu blok çıktığında sistemin bir kaynağın siler güvence altına almak için blok. Bu, büyük miktarda bellek tüketir veya diğer bileşenleri de kullanmak istediğiniz bir sistem kaynağı kullanıyorsanız yararlı olur.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Kodunuz ile sona erdiğinde veritabanı bağlantısını silmek için  
  
1.  Uygun eklediğinizden emin olun [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) başında veritabanı bağlantısının kaynak dosyasının (Bu durumda, <xref:System.Data.SqlClient>).  
  
2.  Oluşturma bir `Using` ile engelleme `Using` ve `End Using` deyimleri. Veritabanı bağlantısı ile ilgilenir kod bloğunun içine yerleştirin.  
  
3.  Bağlantı bildirme ve bir örneğini bir parçası olarak oluşturma `Using` deyimi.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     İşlenmeyen bir özel durum da dahil olmak üzere, blok çıkmak ne olursa olsun kaynağın sistem siler.  
  
     Erişemediğiniz Not `sqc` gelen dışında `Using` kapsamı bloğu ile sınırlı olduğundan engelleyin.  
  
     Bir dosya tanıtıcısı veya bir COM sarmalayıcı gibi bir sistem kaynağı aynı tekniği kullanabilirsiniz. Kullandığınız bir `Using` engelleme emin olmak için çıkış sonra diğer bileşenleri için kullanılabilir kaynak bırakmak istediğinizde `Using` bloğu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.SqlClient.SqlConnection>  
 [Denetim akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Karar yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Döngü yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Diğer denetim yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [İç içe geçmiş denetim yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Using deyimi](../../../../visual-basic/language-reference/statements/using-statement.md)
