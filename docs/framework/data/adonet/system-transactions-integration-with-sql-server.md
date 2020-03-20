---
title: SQL Server ile System.Transactions Tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174244"
---
# <a name="systemtransactions-integration-with-sql-server"></a>SQL Server ile System.Transactions Tümleştirmesi
.NET Framework sürüm <xref:System.Transactions> 2.0, ad alanı üzerinden erişilebilen bir işlem çerçevesi tanıttı. Bu çerçeve, ADO.NET de dahil olmak üzere .NET Çerçevesi'ne tam olarak entegre edilmiş bir şekilde hareketleri ortaya çıkarır.  
  
 Programlanabilirlik geliştirmelerine ek <xref:System.Transactions> olarak ve ADO.NET, hareketlerle çalışırken optimizasyonları koordine etmek için birlikte çalışabilir. Tanıtılabilir işlem, gerektiğinde tam olarak dağıtılmış bir işlemiçin otomatik olarak yükseltilebilen hafif (yerel) bir işlemdir.  
  
 2.0ADO.NET ile <xref:System.Data.SqlClient> başlayarak, SQL Server ile çalışırken tanıtılabilir işlemleri destekler. Eklenebilir bir işlem, eklenen ek yükü gerekli olmadıkça dağıtılmış bir işlemin eklenen ek yükü çağırmaz. Tanıtılabilir işlemler otomatiktir ve geliştiricinin müdahalesi gerektirmez.  
  
 Tanıtılabilir işlemler yalnızca SQL Server için .NET Framework Data`SqlClient`Provider () ile SQL Server ile kullanılabilir.  
  
## <a name="creating-promotable-transactions"></a>Teşvik Edilebilir İşlemler Oluşturma  
 SQL Server için .NET Framework Provider, .NET Framework <xref:System.Transactions> ad alanındaki sınıflar aracılığıyla işlenen teşvik edilebilir hareketler için destek sağlar. Tanıtılabilir hareketler, dağıtılmış bir hareket oluşturmayı gerekli olana kadar erteleyerek dağıtılmış hareketleri en iyi duruma getirin. Yalnızca bir kaynak yöneticisi gerekiyorsa, dağıtılmış hareket oluşmaz.  
  
> [!NOTE]
> Kısmen güvenilen bir senaryoda, <xref:System.Transactions.DistributedTransactionPermission> bir hareket dağıtılmış bir hareket için yükseltildiğinde gereklidir.  
  
## <a name="promotable-transaction-scenarios"></a>Teşvik Edilebilir İşlem Senaryoları  
 Dağıtılmış hareketler genellikle, harekette erişilen tüm kaynak yöneticilerini tümleştiren Microsoft Dağıtılmış Hareket Koordinatörü (MS DTC) tarafından yönetilen önemli sistem kaynaklarını tüketir. Tanıtılabilir işlem, işi basit <xref:System.Transactions> bir SQL Server hareketine etkili bir şekilde devreden özel bir işlem biçimidir. <xref:System.Transactions>, <xref:System.Data.SqlClient>ve SQL Server, hareketi işlemede yer alan işi koordine ederek gerektiğinde tam dağıtılmış bir işleme teşvik etmeyi sağlar.  
  
 Tanıtılabilir hareketleri kullanmanın yararı, bir bağlantı etkin <xref:System.Transactions.TransactionScope> bir işlem kullanılarak açıldığında ve başka bağlantı açılmadığında, hareketin tam dağıtılmış bir işlemin ek ek yüküne maruz kalarak hafif bir işlem olarak işlemesidir.  
  
### <a name="connection-string-keywords"></a>Bağlantı String Anahtar Kelimeler  
 Özellik, <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> `Enlist`işlem bağlamlarını algılayıp <xref:System.Data.SqlClient> algılamayacağını ve dağıtılmış bir hareketteki bağlantıyı otomatik olarak kaydedip kaydetmeyeceğini belirten bir anahtar kelimeyi destekler. `Enlist=true`, bağlantı otomatik olarak açılış iş parçacığının geçerli hareket bağlamında kaydedilir. `Enlist=false`, bağlantı dağıtılmış bir hareketle etkileşime girmiyorsa. `SqlClient` Varsayılan değer `Enlist` doğrudur. Bağlantı `Enlist` dizesinde belirtilmemişse, bağlantı açıldığında biri algılanırsa, bağlantı otomatik olarak dağıtılmış bir harekette kaydedilir.  
  
 Bağlantı dizesindeki anahtar kelimeler, bağlantının `System.Transactions` kayıtlı bir hareketle ilişkisini denetler. `Transaction Binding` <xref:System.Data.SqlClient.SqlConnection> Ayrıca bir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>özelliği üzerinden kullanılabilir .  
  
 Aşağıdaki tabloda olası değerler açıklanmaktadır.  
  
|Anahtar kelime|Açıklama|  
|-------------|-----------------|  
|Örtük Unbind|Varsayılan. Bağlantı sona erdiğinde işlemden ayrılır ve otomatik işleme moduna geri döner.|  
|Açık Unbind|Hareket kapanana kadar bağlantı hareketbağlı kalır. İlişkili hareket etkin değilse veya eşleşmezse <xref:System.Transactions.Transaction.Current%2A>bağlantı başarısız olur.|  
  
## <a name="using-transactionscope"></a>İşlem Kapsamını Kullanma  
 Sınıf, <xref:System.Transactions.TransactionScope> dağıtılmış bir hareketteki bağlantıları dolaylı olarak kaydederek bir kod bloğu hareketi yapar. Ayrılmadan <xref:System.Transactions.TransactionScope.Complete%2A> önce <xref:System.Transactions.TransactionScope> yöntemi bloğun sonundan aramalısınız. Bloğu terk etme <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi çağırır. Kodun kapsam bırakmasına neden olan bir özel durum atılırsa, işlem iptal edilmiş sayılır.  
  
 Kullanma bloğu çıkarıldığında `using` <xref:System.Transactions.TransactionScope.Dispose%2A> <xref:System.Transactions.TransactionScope> nesneüzerinde çağrıldığınızdan emin olmak için bir blok kullanmanızı öneririz. Bekleyen işlemlerin yapılmaması veya geri alınmaması, varsayılan zaman <xref:System.Transactions.TransactionScope> kaybı bir dakika olduğundan performansa önemli ölçüde zarar verebilir. Bir `using` deyim kullanmazsanız, tüm çalışmaları bir `Try` blokta gerçekleştirmeniz <xref:System.Transactions.TransactionScope.Dispose%2A> ve `Finally` yöntemin açıkça blokta çağrılması gerekir.  
  
 Bir özel durum <xref:System.Transactions.TransactionScope>oluşursa, hareket tutarsız olarak işaretlenir ve terk edilir. Bertaraf edildiğinde <xref:System.Transactions.TransactionScope> geri alınır. Bir istisna oluşmazsa, katılımcı hareketler gerçekleşir.  
  
> [!NOTE]
> Sınıf `TransactionScope` varsayılan olarak a <xref:System.Transactions.Transaction.IsolationLevel%2A> `Serializable` ile bir hareket oluşturur. Uygulamanıza bağlı olarak, uygulamanızda yüksek çekişmeyi önlemek için yalıtım düzeyini düşürmeyi düşünebilirsiniz.  
  
> [!NOTE]
> Önemli veritabanı kaynaklarını tükettikleri için yalnızca dağıtılmış hareketler içinde güncelleştirmeler, ekler ve silmeler gerçekleştirmenizi öneririz. Select deyimleri veritabanı kaynaklarını gereksiz yere kilitleyebilir ve bazı senaryolarda, hareketlerin seçim için kullanılması gerekebilir. Diğer işlenen kaynak yöneticileri içermediği sürece, veritabanı dışındaki tüm çalışmalar işlemin kapsamı dışında yapılmalıdır. İşlem kapsamındaki bir özel durum işlemin yapılmasını engellese <xref:System.Transactions.TransactionScope> de, sınıfın kodunuzun hareketin kapsamı dışında yaptığı değişiklikleri geri alma hükmü yoktur. İşlem geri alınırken bazı işlemler yapmak zorundaysanız, <xref:System.Transactions.IEnlistmentNotification> arabirimin kendi uygulamanızı yazmanız ve açıkça harekete kaydolmalısınız.  
  
## <a name="example"></a>Örnek  
 Birlikte <xref:System.Transactions> çalışmak, System.Transactions.dll adresine bir referansıniz olmasını gerektirir.  
  
 Aşağıdaki işlev, bir bloksarılmış iki farklı nesne tarafından temsil edilen iki farklı <xref:System.Data.SqlClient.SqlConnection> SQL Server örneğine karşı <xref:System.Transactions.TransactionScope> nasıl teşvik edilebilir bir işlem oluşturulabilir olduğunu gösterir. Kod bir <xref:System.Transactions.TransactionScope> `using` deyimle bloğu oluşturur ve ilk bağlantıyı açar ve bu <xref:System.Transactions.TransactionScope>bağlantı otomatik olarak . Hareket başlangıçta tam dağıtılmış bir işlem olarak değil, hafif bir işlem olarak kaydedilir. İkinci bağlantı, yalnızca ilk <xref:System.Transactions.TransactionScope> bağlantıdaki komut bir özel durum atmazsa kaydolur. İkinci bağlantı açıldığında, hareket otomatik olarak tam dağıtılmış bir hareket için yükseltilir. Yöntem, <xref:System.Transactions.TransactionScope.Complete%2A> yalnızca özel durumlar atılmadıysa hareketi gerçekleştiren çağrılmıştır. <xref:System.Transactions.TransactionScope> Bloğun herhangi bir noktasında bir özel durum `Complete` atılırsa, çağrılmaz ve dağıtılmış hareket <xref:System.Transactions.TransactionScope> `using` bloğunun sonunda imha edildiğinde geri döner.  
  
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

- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
