---
title: SQL Server ile System.Transactions Tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 25b443d8234909a4d8525c2ce2b4e70c3baa337b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965226"
---
# <a name="systemtransactions-integration-with-sql-server"></a>SQL Server ile System.Transactions Tümleştirmesi
.NET Framework sürüm 2,0, <xref:System.Transactions> ad alanı aracılığıyla erişilebilen bir işlem çerçevesi sunmuştur. Bu çerçeve, ADO.NET dahil olmak üzere .NET Framework, işlemleri tam olarak tümleştirilmiş bir şekilde kullanıma sunar.  
  
 Programlama iyileştirmelerine ek olarak, <xref:System.Transactions> işlemler ile çalışırken iyileştirmeleri koordine etmek için ADO.net birlikte çalışabilir. Bir promotable işlemi, tam olarak dağıtılan bir işlem için gereken bir şekilde otomatik olarak yükseltilabilecek hafif (yerel) bir işlemdir.  
  
 ADO.NET 2,0 ile başlayarak, <xref:System.Data.SqlClient> SQL Server çalışırken promotable işlemlerini destekler. Bir promotable işlemi, eklenen ek yük gerekmediği takdirde dağıtılmış bir işlemin ek yükünü çağırmaz. Promotable işlemleri otomatiktir ve geliştiriciden müdahale gerektirmez.  
  
 Promotable işlemleri yalnızca SQL Server ile SQL Server (`SqlClient`) için .NET Framework veri sağlayıcısı kullandığınızda kullanılabilir.  
  
## <a name="creating-promotable-transactions"></a>Promotable Işlemleri oluşturma  
 SQL Server için .NET Framework sağlayıcısı, .NET Framework <xref:System.Transactions> ad alanındaki sınıflar aracılığıyla işlenen promotable işlemleri için destek sağlar. Promotable işlemleri, dağıtılmış bir işlemin oluşturulması gerekene kadar erteleyerek dağıtılmış işlemleri iyileştirir. Yalnızca bir kaynak yöneticisi gerekliyse, dağıtılmış işlem gerçekleşmez.  
  
> [!NOTE]
> Kısmen güvenilen bir senaryoda <xref:System.Transactions.DistributedTransactionPermission> , bir işlem dağıtılmış bir işleme yükseltildiğinde gereklidir.  
  
## <a name="promotable-transaction-scenarios"></a>Promotable Işlem senaryoları  
 Dağıtılmış işlemler genellikle Microsoft Dağıtılmış İşlem Düzenleyicisi (MS DTC) tarafından yönetilmekte olan önemli sistem kaynaklarını kullanır ve böylece işlem sırasında erişilen tüm kaynak yöneticileri tümleştirilir. Bir promotable işlemi, işi etkin bir şekilde basit <xref:System.Transactions> bir SQL Server işlem olarak temsil eden bir işlemin özel bir biçimidir. <xref:System.Transactions>, <xref:System.Data.SqlClient>ve SQL Server işlem işleme dahil işi koordine etmek ve gerektiğinde tam dağıtılmış bir işleme yükseltmek.  
  
 Promotable işlemlerini kullanmanın avantajı, bir bağlantının etkin <xref:System.Transactions.TransactionScope> bir işlem kullanılarak açıldığı ve başka hiçbir bağlantının açılmadığı durumlarda, işlemin ek bir işlem yapmak yerine hafif bir işlem olarak işleme yaptığı bir işlemdir. tam dağıtılmış işlemin yükü.  
  
### <a name="connection-string-keywords"></a>Bağlantı dizesi anahtar sözcükleri  
 Özelliği, işlem bağlamlarının etkinleştirilip `Enlist`etkinleştirilmeyeceğini ve bağlantıyı dağıtılmış <xref:System.Data.SqlClient> bir işlemde otomatik olarak Enlist olup olmayacağını gösteren bir anahtar sözcüğü destekler. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Varsa `Enlist=true`, bağlantı, açma iş parçacığının geçerli işlem bağlamına otomatik olarak kaydedilir. `Enlist=false` Varsa`SqlClient` , bağlantı dağıtılmış bir işlemle etkileşime girmez. Varsayılan değeri `Enlist` true 'dur. `Enlist` Bağlantı dizesinde belirtilmemişse bağlantı, bağlantı açıldığında algılanan bir dağıtılmış işlemde otomatik olarak kaydedilir.  
  
 `System.Transactions` Bir `Transaction Binding` bağlantıdizesindeki<xref:System.Data.SqlClient.SqlConnection> anahtar sözcükler, kayıtlı bir işlemle bağlantının ilişkilendirmesini denetler. Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>öğesinin özelliği aracılığıyla da kullanılabilir.  
  
 Aşağıdaki tabloda olası değerler açıklanmaktadır.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|Örtük bağlantı kesme|Varsayılan. Bağlantı, sona erdiğinde işlemden ayrıldığında, tekrar tekrar yürütme moduna geçiş yapın.|  
|Açık ciltten çıkarma|İşlem kapatılıncaya kadar bağlantı işleme bağlı kalır. İlişkili işlem etkin değilse veya eşleşmezse <xref:System.Transactions.Transaction.Current%2A>bağlantı başarısız olur.|  
  
## <a name="using-transactionscope"></a>TransactionScope kullanma  
 Sınıfı <xref:System.Transactions.TransactionScope> , dağıtılmış bir işlemdeki bağlantıları örtülü olarak listeleyerek bir kod bloğunu işlem yapar. Uygulamadan çıkmadan önce, <xref:System.Transactions.TransactionScope.Complete%2A> <xref:System.Transactions.TransactionScope> bloğunun sonundaki yöntemini çağırmanız gerekir. Bloğundan ayrıldığınızda <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemini çağırır. Kodun kapsam olmasına neden olan bir özel durum oluşturulursa, işlem durduruldu olarak kabul edilir.  
  
 Using bloğunun çıkış sırasında `using` <xref:System.Transactions.TransactionScope> nesne üzerinde çağrıldığından <xref:System.Transactions.TransactionScope.Dispose%2A> emin olmak için bir blok kullanmanızı öneririz. Bekleyen işlemleri tamamlama veya geri alma hatası, <xref:System.Transactions.TransactionScope> için varsayılan zaman aşımı bir dakika olduğundan performansı önemli ölçüde zarar verebilir. Bir `using` ifade kullanmıyorsanız, tüm işleri bir `Try` <xref:System.Transactions.TransactionScope.Dispose%2A> blokta gerçekleştirmeniz ve `Finally` blok içindeki yöntemi açıkça çağırmanız gerekir.  
  
 İçinde bir özel durum oluşursa <xref:System.Transactions.TransactionScope>, işlem tutarsız olarak işaretlenir ve terk edilir. Bırakıldığında <xref:System.Transactions.TransactionScope> geri alınacaktır. Özel durum oluşursa, katılım işlemleri işleme.  
  
> [!NOTE]
> Sınıfı `TransactionScope` , varsayılan `Serializable` olarak ' a <xref:System.Transactions.Transaction.IsolationLevel%2A> sahip bir işlem oluşturur. Uygulamanıza bağlı olarak, uygulamanızda yüksek çekişmeyi önlemek için yalıtım düzeyini azaltmayı düşünmek isteyebilirsiniz.  
  
> [!NOTE]
> Dağıtılmış işlemler içinde yalnızca güncelleştirme, ekleme ve silme işlemlerini gerçekleştirmenizi öneririz, çünkü bunlar önemli veritabanı kaynakları tüketir. Select deyimleri veritabanı kaynaklarını gereksiz şekilde kilitleyebilir ve bazı senaryolarda, seçim için işlemleri kullanmanız gerekebilir. Veritabanı olmayan herhangi bir iş, diğer işlenen kaynak yöneticilerini içermiyorsa, işlem kapsamı dışında yapılmalıdır. İşlemin kapsamındaki bir özel durum işlemin uygulanmasını engelliyorsa, <xref:System.Transactions.TransactionScope> sınıfın, kodunuzun işlem kapsamı dışında yaptığı tüm değişiklikleri geri almak için bir sağlama yoktur. İşlem geri alındığında biraz işlem yapmanız gerekiyorsa, <xref:System.Transactions.IEnlistmentNotification> arabirimin kendi uygulamanızı yazmanız ve işlem içinde açıkça listelenmesi gerekir.  
  
## <a name="example"></a>Örnek  
 İle <xref:System.Transactions> çalışma, System. Transactions. dll için bir başvuruya sahip olmanızı gerektirir.  
  
 Aşağıdaki işlev, iki farklı SQL Server örneğine karşı, bir <xref:System.Data.SqlClient.SqlConnection> <xref:System.Transactions.TransactionScope> blokta kaydırılan iki farklı nesne ile temsil edilen bir promotable işlemi oluşturmayı gösterir. Kod, <xref:System.Transactions.TransactionScope> bloğu bir `using` ifadesiyle oluşturur ve ' de <xref:System.Transactions.TransactionScope>otomatik olarak listeleyen ilk bağlantıyı açar. İşlem başlangıçta, tam bir dağıtılmış işlem değil, hafif bir işlem olarak kaydedilir. İkinci bağlantı <xref:System.Transactions.TransactionScope> yalnızca ilk bağlantı içindeki komut bir özel durum oluşturmadığından kaydedilir. İkinci bağlantı açıldığında, işlem otomatik olarak tam dağıtılmış bir işleme yükseltilir. <xref:System.Transactions.TransactionScope.Complete%2A> Yöntemi çağrılır, bu işlem yalnızca özel durum atılmadıkça işlemi kaydeder. <xref:System.Transactions.TransactionScope> Bir özel durum, `Complete` bloktaki herhangi bir noktada oluşturulursa, çağrılmaz ve bu, <xref:System.Transactions.TransactionScope> `using` bloğunun sonunda atıldığı zaman dağıtılmış işlem geri alınacaktır.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
