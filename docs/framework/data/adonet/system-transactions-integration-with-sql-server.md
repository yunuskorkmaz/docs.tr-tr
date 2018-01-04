---
title: "SQL Server ile System.Transactions tümleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7765779187156866c20374b60a4b541d36ac9a5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemtransactions-integration-with-sql-server"></a>SQL Server ile System.Transactions tümleştirme
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Üzerinden erişilen bir işlem framework sürüm 2.0 sunulan <xref:System.Transactions> ad alanı. Bu çerçeve işlemleri içinde tam olarak tümleşik bir şekilde kullanıma sunan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]gibi [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 Programlanabilirlik geliştirmeleri yanı sıra <xref:System.Transactions> ve [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] işlemleri ile çalışırken en iyi duruma getirme koordine etmek için birlikte çalışabilir. Otomatik olarak bir tam olarak dağıtılmış işlem gerektiği düzenli olarak yükseltilebilmesi için basit bir (yerel) işlem buna yükseltilebilir bir işlemdir.  
  
 İle başlayarak [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 <xref:System.Data.SqlClient> ile çalışırken yükseltilebilir işlemleri destekler [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Yükseltilebilir işlem eklenen çağrılmaz işlemlerinin ek yükü dağıtılmış işlem eklenen ek yükü gerekli olmadığı sürece. Yükseltilebilir işlemleri otomatik geliştiriciden herhangi bir müdahalesi gerektirir.  
  
 Yükseltilebilir işlemleri yalnızca kullanılabilir kullandığınızda [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için SQL Server veri sağlayıcısı (`SqlClient`) ile [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].  
  
## <a name="creating-promotable-transactions"></a>Yükseltilebilir işlemler oluşturma  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için sağlayıcısı sınıfları aracılığıyla işlenmesini yükseltilebilir işlemler için destek sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> ad alanı. Yükseltilebilir işlemleri gerektiğinde kadar bir dağıtılmış işlem oluşturma ertelemeyi dağıtılmış işlemler en iyi duruma getirme. Yalnızca bir Kaynak Yöneticisi'ni gereklidir, dağıtılmış bir işlem oluşur.  
  
> [!NOTE]
>  Kısmen güvenilen bir senaryoda <xref:System.Transactions.DistributedTransactionPermission> dağıtılmış işlem için bir işlem yükseltildiğinde gereklidir.  
  
## <a name="promotable-transaction-scenarios"></a>Yükseltilebilir işlem senaryoları  
 Dağıtılmış işlemler genellikle Microsoft Dağıtılmış işlem, işlem sırasında erişilen tüm kaynak yöneticileri tümleştirir Düzenleyicisi (MS DTC) tarafından yönetilen önemli sistem kaynaklarını tüketebilir. Yükseltilebilir bir işlem özel bir biçimidir bir <xref:System.Transactions> etkili bir şekilde basit bir işi temsilciler işlem [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] işlem. <xref:System.Transactions>, <xref:System.Data.SqlClient>, ve [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] tam bir dağıtılmış işlem için gerektiği şekilde yükseltme işlemin işlenmesiyle ilgili iş koordinatı.  
  
 Bağlantı etkin bir kullanarak yükseltilebilir işlemleri kullanmanın faydası, açıldığında <xref:System.Transactions.TransactionScope> işlem ve başka bir bağlantı açıldığında, ek yansıtılmasını yerine basit bir işlem olarak işlem yürütme tam bir dağıtılmış işlem yükü.  
  
### <a name="connection-string-keywords"></a>Bağlantı dizesi anahtar sözcükler  
 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Özelliğini destekleyen bir anahtar sözcük `Enlist`, belirten olup olmadığını <xref:System.Data.SqlClient> işlem bağlamları algılar ve otomatik olarak bir dağıtılmış işlemde bağlantıyı kaydolunamadı. Varsa `Enlist=true`, bağlantı otomatik olarak açılırken iş parçacığının geçerli işlem bağlamda kayıtlıdır. Varsa `Enlist=false`, `SqlClient` bağlantı dağıtılmış bir işlem ile etkileşim değil. İçin varsayılan değer `Enlist` doğrudur. Varsa `Enlist` belirtilmezse bağlantı dizesinde bağlantı açıldığında bir algılanırsa, bağlantı bir dağıtılmış işlemde otomatik olarak kayıtlı.  
  
 `Transaction Binding` Anahtar bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesini kontrol bir kayıtlı olan bağlantının ilişkilendirmesini `System.Transactions` işlem. Ayrıca aracılığıyla kullanılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> özelliği bir <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Aşağıdaki tabloda olası değerleri açıklanmaktadır.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|Örtük bağlantı kesme|Varsayılan. Otomatik kayıt işlemleri moduna geçiriliyor sona erdiğinde bağlantıyı işleminden ayırır.|  
|Açık bağlantı kesme|İşlem kapatılana kadar bağlantı harekete eklenen kalır. İlişkili işlem etkin değil veya eşleşmiyor bağlantı başarısız olur <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>TransactionScope kullanma  
 <xref:System.Transactions.TransactionScope> Sınıfı yapacağı kod bloğu işlem örtük olarak bir dağıtılmış işlemde bağlantıları kaydetme tarafından. Çağırmalısınız <xref:System.Transactions.TransactionScope.Complete%2A> sonunda yöntemi <xref:System.Transactions.TransactionScope> , çıkmadan önce bloğu. Blok bırakarak çağırır <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi. Kod kapsamı, işlem bırakın kabul neden iptal edildiğini bir özel durum oluşturuldu  
  
 Kullanmanızı öneririz bir `using` emin olmak için blok <xref:System.Transactions.TransactionScope.Dispose%2A> üzerinde adlı <xref:System.Transactions.TransactionScope> nesnesi kullanarak ne zaman engelleme çıkıldı. Yürütme veya geri işlemler için hata önemli ölçüde zarar performans çünkü için varsayılan zaman aşımı <xref:System.Transactions.TransactionScope> bir dakikadır. Kullanmıyorsanız, bir `using` deyimi, tüm iş gerçekleştirmelisiniz bir `Try` engellemek ve açıkça çağırın <xref:System.Transactions.TransactionScope.Dispose%2A> yönteminde `Finally` bloğu.  
  
 Bir özel durum oluşması halinde <xref:System.Transactions.TransactionScope>, işlem tutarsız olarak işaretlenir ve terk edilir. Bunu alınacak ne zaman geri <xref:System.Transactions.TransactionScope> atıldı. Hiçbir özel durum oluşursa, katılımcı işlemler uygulayın.  
  
> [!NOTE]
>  `TransactionScope` Sınıfı oluşturur bir işlemle bir <xref:System.Transactions.Transaction.IsolationLevel%2A> , `Serializable` varsayılan olarak. Uygulamanızın bağlı olarak, uygulamanızda yüksek çekişmesinden kaçınmak için yalıtım düzeyini düşünmek isteyebilirsiniz.  
  
> [!NOTE]
>  Yalnızca güncelleştirmeleri ekler, gerçekleştirme ve önemli veritabanı kaynaklarını tükettiği için siler içinde dağıtılmış işlemler öneririz. SELECT deyimi veritabanı kaynakları gereksiz yere Kilitle ve bazı senaryolarda, işlemler için seçer kullanmak zorunda kalabilirsiniz. Diğer işlem temelli kaynak yöneticileri içerir sürece herhangi bir veritabanı olmayan iş hareket kapsamı dışında yapılmalıdır. Kapsamdaki istisna hareketin gerçekleştirmeden, gelen işlem engeller rağmen <xref:System.Transactions.TransactionScope> sınıfı işlem kapsamı dışında herhangi bir değişiklik kodunuzun geri yaptı için hiçbir sağlama sahiptir. İşlem geri alındı, bazı işlemler yapması varsa, kendi uygulamanızı yazma <xref:System.Transactions.IEnlistmentNotification> arabirim ve açıkça işleminde listelenmeyi.  
  
## <a name="example"></a>Örnek  
 İle çalışma <xref:System.Transactions> System.Transactions.dll başvuru sahip olmasını gerektirir.  
  
 Aşağıdaki işlevi nasıl iki tarafından temsil edilen, iki farklı SQL Server örnekleri karşı yükseltilebilir işlem farklı oluşturulduğunu gösteren <xref:System.Data.SqlClient.SqlConnection> kaydırılır nesneleri bir <xref:System.Transactions.TransactionScope> bloğu. Kod oluşturur <xref:System.Transactions.TransactionScope> ile engelleme bir `using` deyimi ve otomatik olarak içinde kaydeder ilk bağlantı açar <xref:System.Transactions.TransactionScope>. İşlem, başlangıçta, tam bir dağıtılmış işlem yok gibi basit bir işlem olarak kayıtlıdır. İkinci bir bağlantı olarak kayıtlıdır <xref:System.Transactions.TransactionScope> varsa yalnızca ilk bağlantı komutta bir özel durum oluşturmaz. İkinci bir bağlantı açıldığında, işlem için tam bir dağıtılmış işlem otomatik olarak yükseltilir. <xref:System.Transactions.TransactionScope.Complete%2A> Yöntemi çağrıldığında, yalnızca hiçbir özel durum, hangi hareketi tamamlar. İçinde herhangi bir noktada bir özel durum oluşturuldu, <xref:System.Transactions.TransactionScope> bloğu `Complete` değil çağrılması olacaktır ve alma dağıtılmış işlem ne zaman geri <xref:System.Transactions.TransactionScope> sonunda atıldı kendi `using` bloğu.  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
