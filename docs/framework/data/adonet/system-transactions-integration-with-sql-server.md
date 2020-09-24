---
title: SQL Server ile System.Transactions Tümleştirmesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 5adf40f96854e08736cdef77300d69e452de5eea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191690"
---
# <a name="systemtransactions-integration-with-sql-server"></a>SQL Server ile System.Transactions Tümleştirmesi

.NET Framework sürüm 2,0, ad alanı aracılığıyla erişilebilen bir işlem çerçevesi sunmuştur <xref:System.Transactions> . Bu çerçeve, ADO.NET dahil olmak üzere .NET Framework, işlemleri tam olarak tümleştirilmiş bir şekilde kullanıma sunar.  
  
 Programlama iyileştirmelerine ek olarak, <xref:System.Transactions> işlemler ile çalışırken iyileştirmeleri koordine etmek için ADO.net birlikte çalışabilir. Bir promotable işlemi, tam olarak dağıtılan bir işlem için gereken bir şekilde otomatik olarak yükseltilabilecek hafif (yerel) bir işlemdir.  
  
 ADO.NET 2,0 ile başlayarak, <xref:System.Data.SqlClient> SQL Server çalışırken promotable işlemlerini destekler. Bir promotable işlemi, eklenen ek yük gerekmediği takdirde dağıtılmış bir işlemin ek yükünü çağırmaz. Promotable işlemleri otomatiktir ve geliştiriciden müdahale gerektirmez.  
  
 Promotable işlemleri yalnızca SQL Server ile SQL Server () için .NET Framework Veri Sağlayıcısı kullandığınızda kullanılabilir `SqlClient` .  
  
## <a name="creating-promotable-transactions"></a>Promotable Işlemleri oluşturma  

 SQL Server için .NET Framework sağlayıcısı, .NET Framework ad alanındaki sınıflar aracılığıyla işlenen promotable işlemleri için destek sağlar <xref:System.Transactions> . Promotable işlemleri, dağıtılmış bir işlemin oluşturulması gerekene kadar erteleyerek dağıtılmış işlemleri iyileştirir. Yalnızca bir kaynak yöneticisi gerekliyse, dağıtılmış işlem gerçekleşmez.  
  
> [!NOTE]
> Kısmen güvenilen bir senaryoda, <xref:System.Transactions.DistributedTransactionPermission> bir işlem dağıtılmış bir işleme yükseltildiğinde gereklidir.  
  
## <a name="promotable-transaction-scenarios"></a>Promotable Işlem senaryoları  

 Dağıtılmış işlemler genellikle Microsoft Dağıtılmış İşlem Düzenleyicisi (MS DTC) tarafından yönetilmekte olan önemli sistem kaynaklarını kullanır ve böylece işlem sırasında erişilen tüm kaynak yöneticileri tümleştirilir. Bir promotable işlemi, <xref:System.Transactions> işi etkin bir şekilde basit bir SQL Server işlem olarak temsil eden bir işlemin özel bir biçimidir. <xref:System.Transactions>, <xref:System.Data.SqlClient> ve SQL Server işlem işleme dahil işi koordine etmek ve gerektiğinde tam dağıtılmış bir işleme yükseltmek.  
  
 Promotable işlemleri kullanmanın avantajı, bir bağlantının etkin bir işlem kullanılarak açıldığı <xref:System.Transactions.TransactionScope> ve başka hiçbir bağlantının açılmadığı durumlarda, bir tam dağıtılmış işlemin ek yükünü ortadan kaldırarak, işlemin hafif bir işlem olarak işlemeleridir.  
  
### <a name="connection-string-keywords"></a>Bağlantı dizesi anahtar sözcükleri  

 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>Özelliği, `Enlist` <xref:System.Data.SqlClient> işlem bağlamlarının etkinleştirilip etkinleştirilmeyeceğini ve bağlantıyı dağıtılmış bir işlemde otomatik olarak Enlist olup olmayacağını gösteren bir anahtar sözcüğü destekler. Varsa `Enlist=true` , bağlantı, açma iş parçacığının geçerli işlem bağlamına otomatik olarak kaydedilir. Varsa `Enlist=false` , `SqlClient` bağlantı dağıtılmış bir işlemle etkileşime girmez. Varsayılan değeri `Enlist` true 'dur. Bağlantı `Enlist` dizesinde belirtilmemişse bağlantı, bağlantı açıldığında algılanan bir dağıtılmış işlemde otomatik olarak kaydedilir.  
  
 `Transaction Binding`Bir bağlantı dizesindeki anahtar sözcükler, <xref:System.Data.SqlClient.SqlConnection> kayıtlı bir işlemle bağlantının ilişkilendirmesini denetler `System.Transactions` . Ayrıca, öğesinin özelliği aracılığıyla da kullanılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder> .  
  
 Aşağıdaki tabloda olası değerler açıklanmaktadır.  
  
|Sözcükle|Açıklama|  
|-------------|-----------------|  
|Örtük bağlantı kesme|Varsayılan. Bağlantı, sona erdiğinde işlemden ayrıldığında, tekrar tekrar yürütme moduna geçiş yapın.|  
|Açık ciltten çıkarma|İşlem kapatılıncaya kadar bağlantı işleme bağlı kalır. İlişkili işlem etkin değilse veya eşleşmezse bağlantı başarısız olur <xref:System.Transactions.Transaction.Current%2A> .|  
  
## <a name="using-transactionscope"></a>TransactionScope kullanma  

 <xref:System.Transactions.TransactionScope>Sınıfı, dağıtılmış bir işlemdeki bağlantıları örtülü olarak listeleyerek bir kod bloğunu işlem yapar. <xref:System.Transactions.TransactionScope.Complete%2A>Uygulamadan çıkmadan önce, bloğunun sonundaki yöntemini çağırmanız gerekir <xref:System.Transactions.TransactionScope> . Bloğundan ayrıldığınızda yöntemini çağırır <xref:System.Transactions.TransactionScope.Dispose%2A> . Kodun kapsam olmasına neden olan bir özel durum oluşturulursa, işlem durduruldu olarak kabul edilir.  
  
 `using` <xref:System.Transactions.TransactionScope.Dispose%2A> <xref:System.Transactions.TransactionScope> Using bloğunun çıkış sırasında nesne üzerinde çağrıldığından emin olmak için bir blok kullanmanızı öneririz. Bekleyen işlemleri tamamlama veya geri alma hatası, için varsayılan zaman aşımı bir dakika olduğundan performansı önemli ölçüde zarar verebilir <xref:System.Transactions.TransactionScope> . Bir `using` ifade kullanmıyorsanız, tüm işleri bir `Try` blokta gerçekleştirmeniz ve <xref:System.Transactions.TransactionScope.Dispose%2A> blok içindeki yöntemi açıkça çağırmanız gerekir `Finally` .  
  
 İçinde bir özel durum oluşursa <xref:System.Transactions.TransactionScope> , işlem tutarsız olarak işaretlenir ve terk edilir. Bırakıldığında geri alınacaktır <xref:System.Transactions.TransactionScope> . Özel durum oluşursa, katılım işlemleri işleme.  
  
> [!NOTE]
> `TransactionScope`Sınıfı, <xref:System.Transactions.Transaction.IsolationLevel%2A> Varsayılan olarak ' a sahip bir işlem oluşturur `Serializable` . Uygulamanıza bağlı olarak, uygulamanızda yüksek çekişmeyi önlemek için yalıtım düzeyini azaltmayı düşünmek isteyebilirsiniz.  
  
> [!NOTE]
> Dağıtılmış işlemler içinde yalnızca güncelleştirme, ekleme ve silme işlemlerini gerçekleştirmenizi öneririz, çünkü bunlar önemli veritabanı kaynakları tüketir. Select deyimleri veritabanı kaynaklarını gereksiz şekilde kilitleyebilir ve bazı senaryolarda, seçim için işlemleri kullanmanız gerekebilir. Veritabanı olmayan herhangi bir iş, diğer işlenen kaynak yöneticilerini içermiyorsa, işlem kapsamı dışında yapılmalıdır. İşlemin kapsamındaki bir özel durum işlemin uygulanmasını engelliyorsa, <xref:System.Transactions.TransactionScope> sınıfın, kodunuzun işlem kapsamı dışında yaptığı tüm değişiklikleri geri almak için bir sağlama yoktur. İşlem geri alındığında biraz işlem yapmanız gerekiyorsa, arabirimin kendi uygulamanızı yazmanız <xref:System.Transactions.IEnlistmentNotification> ve işlem içinde açıkça listelenmesi gerekir.  
  
## <a name="example"></a>Örnek  

 İle çalışma <xref:System.Transactions> , System.Transactions.dll bir başvuruya sahip olmanızı gerektirir.  
  
 Aşağıdaki işlev, iki farklı SQL Server örneğine karşı, bir blokta kaydırılan iki farklı nesne ile temsil edilen bir promotable işlemi oluşturmayı gösterir <xref:System.Data.SqlClient.SqlConnection> <xref:System.Transactions.TransactionScope> . Kod, <xref:System.Transactions.TransactionScope> bloğu bir `using` ifadesiyle oluşturur ve ' de otomatik olarak listeleyen ilk bağlantıyı açar <xref:System.Transactions.TransactionScope> . İşlem başlangıçta, tam bir dağıtılmış işlem değil, hafif bir işlem olarak kaydedilir. İkinci bağlantı <xref:System.Transactions.TransactionScope> yalnızca ilk bağlantı içindeki komut bir özel durum oluşturmadığından kaydedilir. İkinci bağlantı açıldığında, işlem otomatik olarak tam dağıtılmış bir işleme yükseltilir. <xref:System.Transactions.TransactionScope.Complete%2A>Yöntemi çağrılır, bu işlem yalnızca özel durum atılmadıkça işlemi kaydeder. Bir özel durum, bloktaki herhangi bir noktada oluşturulursa, <xref:System.Transactions.TransactionScope> `Complete` çağrılmaz ve bu, <xref:System.Transactions.TransactionScope> bloğunun sonunda atıldığı zaman dağıtılmış işlem geri alınacaktır `using` .  
  
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
