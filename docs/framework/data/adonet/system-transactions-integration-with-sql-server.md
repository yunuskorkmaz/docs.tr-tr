---
title: SQL Server ile System.Transactions tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 12b81d02e5db613c96d19a4aa3730b95e3477b7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558624"
---
# <a name="systemtransactions-integration-with-sql-server"></a>SQL Server ile System.Transactions tümleştirmesi
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Sürüm 2.0 kullanılmaya aracılığıyla erişilebilen bir işlem framework <xref:System.Transactions> ad alanı. Bu çerçeve işlemleri, tamamen tümleşik bir şekilde kullanıma sunan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]de dahil olmak üzere [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 Programlanabilirlik geliştirmeleri yanı sıra <xref:System.Transactions> ve [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] işlemleri ile çalışırken en iyi duruma getirme koordine etmek için birlikte çalışabilir. Otomatik olarak tam olarak dağıtılmış bir işlem gerekli olarak yükseltilebilir basit bir (yerel) işlem bir promotable işlemdir.  
  
 İle başlayarak [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 <xref:System.Data.SqlClient> SQL Server ile çalışırken promotable işlemleri destekler. Bir promotable işlem eklenen çağırmadığı işlemlerinin ek yükü dağıtılmış işlem ek yükü gerekli olmadığı sürece. Promotable işlemleri otomatik olarak yapılır ve geliştiriciden herhangi bir müdahalesi gerektirir.  
  
 Promotable işlemleri bulunan ve yalnızca kullandığınız zaman [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için veri sağlayıcısı (`SqlClient`) SQL Server ile.  
  
## <a name="creating-promotable-transactions"></a>Promotable işlemleri oluşturma  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için sağlayıcısı sınıfları aracılığıyla işlenir promotable işlemler için destek sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> ad alanı. Promotable işlemleri, gerekli olana kadar bir dağıtılmış işlem oluşturma erteleyerek dağıtılmış işlemler iyileştirin. Yalnızca biri resource manager gerekliyse, hiçbir dağıtılmış işlem gerçekleşir.  
  
> [!NOTE]
>  Kısmen güvenilen bir senaryoda <xref:System.Transactions.DistributedTransactionPermission> dağıtılmış bir işlem için bir işlem yükseltildiğinde gereklidir.  
  
## <a name="promotable-transaction-scenarios"></a>Promotable işlem senaryoları  
 Dağıtılmış işlemler genellikle Microsoft Dağıtılmış işlem işlemde erişilen tüm kaynak yöneticileri tümleşen Düzenleyicisi (MS DTC) tarafından yönetilen önemli sistem kaynaklarını kullanır. Özel bir promotable harekettir bir <xref:System.Transactions> etkili bir şekilde basit bir SQL Server işlem işi temsilciler işlem. <xref:System.Transactions>, <xref:System.Data.SqlClient>, ve SQL Server, tam bir dağıtılmış işlem için gereken şekilde yükseltmek işlem işlenmesiyle ilgili iş koordine etmek.  
  
 Bir bağlantı etkin bir kullanarak promotable işlemleri kullanmanın avantajı, açıldığında <xref:System.Transactions.TransactionScope> işlem ve başka bir bağlantı açıldığında, ek sunucular yerine basit bir işlem olarak işlem yürütmeleri tam bir dağıtılmış işlem ek yükü.  
  
### <a name="connection-string-keywords"></a>Bağlantı dizesi anahtar sözcükleri  
 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Özelliğini destekleyen bir anahtar sözcük `Enlist`, gösteren olmadığını <xref:System.Data.SqlClient> işlem bağlamları algılar ve bir dağıtılmış işlem bağlantı otomatik olarak listeleme. Varsa `Enlist=true`, bağlantı otomatik olarak açılırken iş parçacığının geçerli işlem bağlamında kayıtlıdır. Varsa `Enlist=false`, `SqlClient` bağlantı ile dağıtılmış bir işlem etkileşimli değil. İçin varsayılan değer `Enlist` geçerlidir. Varsa `Enlist` belirtilmezse bağlantı dizesinde bağlantıyı açıldığında bir algılanırsa bağlantı dağıtılmış bir işlem içinde otomatik olarak kayıtlı.  
  
 `Transaction Binding` Anahtar bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesini kontrol kayıtlı bir bağlantının ilişkilendirmesini `System.Transactions` işlem. Ayrıca aracılığıyla <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> özelliği bir <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Olası değerler aşağıdaki tabloda açıklanmaktadır.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|Örtük Unbind|Varsayılan. Commıtted moduna geçiş sona erdiğinde bağlantıyı bir işlemden ayırır.|  
|Açık Unbind|İşlem kapatılana kadar bağlantı harekete iliştirilmiş olarak kalır. Bağlantı başarısız olur, ilişkili işlem etkin değil ya da eşleşmiyor <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>TransactionScope kullanma  
 <xref:System.Transactions.TransactionScope> Sınıfı yapacağı bir kod bloğu işlem bir dağıtılmış işlemde bağlantı kaydetme tarafından örtük olarak. Çağırmalısınız <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi sonunda <xref:System.Transactions.TransactionScope> , çıkmadan önce blok. Blok bırakarak çağırır <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi. Kod kapsamı, işlem bırakmak kabul neden iptal edildiğini bir özel durumun durumunda.  
  
 Kullanmanızı öneririz bir `using` emin olmak için blok <xref:System.Transactions.TransactionScope.Dispose%2A> üzerinde çağrılır <xref:System.Transactions.TransactionScope> nesnesini kullanarak engelliyken çıkıldı. Hata işleme veya işlemleri geri önemli ölçüde zarar performans çünkü için varsayılan zaman aşımı <xref:System.Transactions.TransactionScope> bir dakikadır. Kullanmıyorsanız, bir `using` deyimi, tüm iş gerçekleştirmelisiniz bir `Try` engelleme ve açıkça çağırmak <xref:System.Transactions.TransactionScope.Dispose%2A> yönteminde `Finally` blok.  
  
 Bir özel durum oluşursa <xref:System.Transactions.TransactionScope>, işlem tutarsız olarak işaretlenir ve terk edilir. Kullanıma sunulacak geri <xref:System.Transactions.TransactionScope> atıldı. Hiçbir özel durum oluşursa, katılımcı işlemleri işleyin.  
  
> [!NOTE]
>  `TransactionScope` Sınıfı ile bir işlem oluşturur bir <xref:System.Transactions.Transaction.IsolationLevel%2A> , `Serializable` varsayılan olarak. Uygulamanızın bağlı olarak, uygulamanızda yüksek çekişmesinden kaçınmak için yalıtım düzeyini düşünmek isteyebilirsiniz.  
  
> [!NOTE]
>  Yalnızca güncelleştirmeleri ekler, gerçekleştirme ve önemli veritabanı kaynakları kullandıkları çünkü siler içinde dağıtılmış işlemler öneririz. SELECT deyimleri veritabanı kaynaklarının gereksiz yere Kilitle ve bazı senaryolarda, işlemler için seçer kullanmak zorunda kalabilirsiniz. Diğer işlenen kaynak yöneticileri içerdiği sürece işlem kapsamı dışında herhangi bir veritabanı olmayan iş yapılmalıdır. İşlem kapsamı içindeki bir özel durum işleme, gelen işlem engeller ancak <xref:System.Transactions.TransactionScope> değişikliklerin, kodunuzun geri işlem kapsamı dışında hale getirdiği için hiçbir sınıfı vardır. İşlem geri alınır, bazı işlemler yapması gerekiyorsa, kendi uygulamasını yazmanız gereken <xref:System.Transactions.IEnlistmentNotification> arabirim ve açıkça işleme.  
  
## <a name="example"></a>Örnek  
 Çalışma <xref:System.Transactions> System.Transactions.dll başvurusu olmasını gerektirir.  
  
 Aşağıdaki işlevi bir promotable işlem iki tarafından temsil edilen iki farklı SQL Server örneği karşı farklı nasıl oluşturulacağını gösterir <xref:System.Data.SqlClient.SqlConnection> sarmalanır nesneleri, bir <xref:System.Transactions.TransactionScope> blok. Kod oluşturur <xref:System.Transactions.TransactionScope> ile engelleyecek bir `using` deyimi içinde otomatik olarak kaydeder ilk bağlantıyı açar <xref:System.Transactions.TransactionScope>. İşlem başlangıçta, tam bir dağıtılmış işlem yok gibi basit bir işlem olarak kayıtlıdır. İkinci bir bağlantı kayıtlı <xref:System.Transactions.TransactionScope> varsa yalnızca ilk bağlantı komut bir özel durum oluşturmaz. İkinci bağlantı açıldığında, işlem bir tam dağıtılmış işlem için otomatik olarak yükseltilir. <xref:System.Transactions.TransactionScope.Complete%2A> Yöntemi çağrılır, eğer yalnızca hiçbir özel durum harekete hangi hareketi tamamlar. Herhangi bir noktada bir özel durum oluştuktan varsa <xref:System.Transactions.TransactionScope> bloğu `Complete` değil çağrılması sağlar ve geri dağıtılmış işlem olacak geri <xref:System.Transactions.TransactionScope> sonunda elden kendi `using` blok.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
