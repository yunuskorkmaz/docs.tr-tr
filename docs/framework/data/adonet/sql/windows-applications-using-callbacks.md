---
title: Geri çağırmaları kullanarak Windows uygulamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ae2ea457-0764-4b06-8977-713c77e85bd2
ms.openlocfilehash: 9f1e3fe6d53266a4e1366c1a3d5396688a25df0f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517658"
---
# <a name="windows-applications-using-callbacks"></a><span data-ttu-id="570cf-102">Geri çağırmaları kullanarak Windows uygulamaları</span><span class="sxs-lookup"><span data-stu-id="570cf-102">Windows Applications Using Callbacks</span></span>
<span data-ttu-id="570cf-103">Çoğu zaman uyumsuz işleme senaryoda, bir veritabanı işlemi başlatmak ve veritabanı işlemin tamamlanmasını beklemenize gerek kalmadan çalışan diğer işlemlerin devam etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="570cf-103">In most asynchronous processing scenarios, you want to start a database operation and continue running other processes without waiting for the database operation to complete.</span></span> <span data-ttu-id="570cf-104">Ancak, veritabanı işlemi sona erdikten sonra şeyi yapmanın birçok senaryo gerektirir.</span><span class="sxs-lookup"><span data-stu-id="570cf-104">However, many scenarios require doing something once the database operation has ended.</span></span> <span data-ttu-id="570cf-105">Örneğin, bir Windows uygulamasında kullanıcı arabirimi iş parçacığı yanıt verebilir durumda kalmasını sağlarken uzun süre çalışan işlemi bir arka plan iş parçacığı için temsilci seçmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="570cf-105">In a Windows application, for example, you may want to delegate the long-running operation to a background thread while allowing the user interface thread to remain responsive.</span></span> <span data-ttu-id="570cf-106">Ancak, veritabanı işlemi tamamlandığında, sonuçları formun doldurulması için kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="570cf-106">However, when the database operation is complete, you want to use the results to populate the form.</span></span> <span data-ttu-id="570cf-107">Bu tür bir senaryo, bir geri çağırma ile en iyi şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="570cf-107">This type of scenario is best implemented with a callback.</span></span>  
  
 <span data-ttu-id="570cf-108">Belirterek bir geri çağırma tanımladığınız bir <xref:System.AsyncCallback> içindeki temsilci <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, veya <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="570cf-108">You define a callback by specifying an <xref:System.AsyncCallback> delegate in the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, or <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> method.</span></span> <span data-ttu-id="570cf-109">İşlem tamamlandığında, bir temsilci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="570cf-109">The delegate is called when the operation is complete.</span></span> <span data-ttu-id="570cf-110">Temsilci bir başvuru geçirebilirsiniz <xref:System.Data.SqlClient.SqlCommand> erişimi kolaylaştıran kendisini <xref:System.Data.SqlClient.SqlCommand> nesne ve uygun çağrı `End` genel değişken kullanmak zorunda kalmadan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="570cf-110">You can pass the delegate a reference to the <xref:System.Data.SqlClient.SqlCommand> itself, making it easy to access the <xref:System.Data.SqlClient.SqlCommand> object and call the appropriate `End` method without having to use a global variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="570cf-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="570cf-111">Example</span></span>  
 <span data-ttu-id="570cf-112">Aşağıdaki Windows uygulama kullanımını gösteren <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> yöntemi, birkaç saniye (bir uzun süre çalışan komut öykünen) bir gecikme içeren bir Transact-SQL deyimi yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="570cf-112">The following Windows application demonstrates the use of the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> method, executing a Transact-SQL statement that includes a delay of a few seconds (emulating a long-running command).</span></span>  
  
 <span data-ttu-id="570cf-113">Bu örnek, bir dizi ayrı bir iş parçacığından formla etkileşime giren bir yöntemi çağırmak dahil olmak üzere önemli teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="570cf-113">This example demonstrates a number of important techniques, including calling a method that interacts with the form from a separate thread.</span></span> <span data-ttu-id="570cf-114">Ayrıca, bu örnek aynı anda birden çok kez komut yürütme kullanıcıların nasıl engellemelisiniz gösterir ve nasıl formun önce geri çağırma yordamı kapatmaz emin olmanız gerekir çağrılır.</span><span class="sxs-lookup"><span data-stu-id="570cf-114">In addition, this example demonstrates how you must block users from concurrently executing a command multiple times, and how you must ensure that the form does not close before the callback procedure is called.</span></span>  
  
 <span data-ttu-id="570cf-115">Bu örnekte ayarlamak için yeni bir Windows uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="570cf-115">To set up this example, create a new Windows application.</span></span> <span data-ttu-id="570cf-116">Bir yerde bir <xref:System.Windows.Forms.Button> denetimi ve iki <xref:System.Windows.Forms.Label> (her denetim için varsayılan adı kabul etme) form üzerinde denetimleri.</span><span class="sxs-lookup"><span data-stu-id="570cf-116">Place a <xref:System.Windows.Forms.Button> control and two <xref:System.Windows.Forms.Label> controls on the form (accepting the default name for each control).</span></span> <span data-ttu-id="570cf-117">Ortamınız için gerektiği gibi bağlantı dizesini değiştirerek formun sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="570cf-117">Add the following code to the form's class, modifying the connection string as necessary for your environment.</span></span>  
  
```vb  
' Add these to the top of the class:  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
' Add this code to the form's class:  
  
    ' You'll need this delegate in order to display text from a   
    ' thread other than the form's thread. See the HandleCallback  
    ' procedure for more information.  
    ' This same delegate matches both the DisplayStatus   
    ' and DisplayResults methods.  
    Private Delegate Sub DisplayInfoDelegate(ByVal Text As String)  
  
    ' This flag ensures that the user doesn't attempt  
    ' to restart the command or close the form while the   
    ' asynchronous command is executing.  
    Private isExecuting As Boolean  
  
    ' This example maintains the connection object   
    ' externally, so that it's available for closing.  
    Private connection As SqlConnection  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,              
        ' you can retrieve it from a configuration file.   
  
        ' If you have not included "Asynchronous Processing=true"  
        ' in the connection string, the command will not be able  
        ' to execute asynchronously.  
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks;" & _  
          "Asynchronous Processing=true"  
    End Function  
  
    Private Sub DisplayStatus(ByVal Text As String)  
        Me.Label1.Text = Text  
    End Sub  
  
    Private Sub DisplayResults(ByVal Text As String)  
        Me.Label1.Text = Text  
        DisplayStatus("Ready")  
    End Sub  
  
    Private Sub Form1_FormClosing(ByVal sender As Object, _  
        ByVal e As System.Windows.Forms.FormClosingEventArgs) _  
        Handles Me.FormClosing  
        If isExecuting Then  
            MessageBox.Show(Me, "Can't close the form until " & _  
             "the pending asynchronous command has completed. " & _  
             "Please wait...")  
            e.Cancel = True  
        End If  
    End Sub  
  
    Private Sub Button1_Click( _  
        ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles Button1.Click  
        If isExecuting Then  
            MessageBox.Show(Me, _  
                "Already executing. " & _  
                "Please wait until the current query " & _  
                "has completed.")  
        Else  
            Dim command As SqlCommand  
            Try  
                DisplayResults("")  
                DisplayStatus("Connecting...")  
                connection = New SqlConnection(GetConnectionString())  
                ' To emulate a long-running query, wait for   
                ' a few seconds before working with the data.  
                ' This command doesn't do much, but that's the point--  
                ' it doesn't change your data, in the long run.  
                Dim commandText As String = _  
                    "WAITFOR DELAY '0:0:05';" & _  
                    "UPDATE Production.Product " & _  
                    "SET ReorderPoint = ReorderPoint + 1 " & _  
                    "WHERE ReorderPoint Is Not Null;" & _  
                    "UPDATE Production.Product " & _  
                    "SET ReorderPoint = ReorderPoint - 1 " & _  
                    "WHERE ReorderPoint Is Not Null"  
  
                command = New SqlCommand(commandText, connection)  
                connection.Open()  
  
                DisplayStatus("Executing...")  
                isExecuting = True  
                ' Although it's not required that you pass the   
                ' SqlCommand object as the second parameter in the   
                ' BeginExecuteNonQuery call, doing so makes it easier  
                ' to call EndExecuteNonQuery in the callback procedure.  
                Dim callback As New _  
                      AsyncCallback(AddressOf HandleCallback)  
  
                ' Once the BeginExecuteNonQuery method is called,  
                ' the code continues--and the user can interact with  
                ' the form--while the server executes the query.  
  
                command.BeginExecuteNonQuery(callback, command)  
  
            Catch ex As Exception  
                isExecuting = False  
                DisplayStatus( _  
                    String.Format("Ready (last error: {0})", _  
                    ex.Message))  
                If connection IsNot Nothing Then  
                    connection.Close()  
                End If  
            End Try  
        End If  
    End Sub  
  
    Private Sub HandleCallback(ByVal result As IAsyncResult)  
        Try  
            ' Retrieve the original command object, passed  
            ' to this procedure in the AsyncState property  
            ' of the IAsyncResult parameter.  
            Dim command As SqlCommand = _  
                CType(result.AsyncState, SqlCommand)  
            Dim rowCount As Integer = _  
                command.EndExecuteNonQuery(result)  
            Dim rowText As String = " rows affected."  
            If rowCount = 1 Then  
                rowText = " row affected."  
            End If  
            rowText = rowCount & rowText  
  
            ' You may not interact with the form and its contents  
            ' from a different thread, and this callback procedure  
            ' is all but guaranteed to be running from a different   
            ' thread than the form. Therefore you cannot simply call   
            ' code that displays the results, like this:  
            ' DisplayResults(rowText)  
  
            ' Instead, you must call the procedure from the form's  
            ' thread. One simple way to accomplish this is to call   
            ' the Invoke method of the form, which calls the delegate   
            ' you supply from the form's thread.   
            Dim del As New _  
                DisplayInfoDelegate(AddressOf DisplayResults)  
            Me.Invoke(del, rowText)  
  
        Catch ex As Exception  
            ' Because you're now running code in a separate thread,   
            ' if you don't handle the exception here, none of your   
            ' other code will catch the exception. Because none of   
            ' your code is on the call stack in this thread, there's   
            ' nothing higher up the stack to catch the exception if   
            ' you don't handle it here. You can either log the   
            ' exception or invoke a delegate (as in the non-error   
            ' case in this example) to display the error on the form.   
            ' In no case can you simply display the error without   
            ' executing a delegate as in the Try block here.  
  
            ' You can create the delegate instance as you   
            ' invoke it, like this:  
            Me.Invoke(New _  
                DisplayInfoDelegate(AddressOf DisplayStatus), _  
                String.Format("Ready(last error: {0}", ex.Message))  
        Finally  
            isExecuting = False  
            If connection IsNot Nothing Then  
                connection.Close()  
            End If  
        End Try  
    End Sub  
```  
  
```csharp  
// Add these to the top of the class, if they're not already there:  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
// Hook up the form's Load event handler (you can double-click on   
// the form's design surface in Visual Studio), and then add   
// this code to the form's class:  
  
// You'll need this delegate in order to display text from a thread  
// other than the form's thread. See the HandleCallback  
// procedure for more information.  
// This same delegate matches both the DisplayStatus   
// and DisplayResults methods.  
private delegate void DisplayInfoDelegate(string Text);  
  
// This flag ensures that the user doesn't attempt  
// to restart the command or close the form while the   
// asynchronous command is executing.  
private bool isExecuting;  
  
// This example maintains the connection object   
// externally, so that it's available for closing.  
private SqlConnection connection;  
  
private static string GetConnectionString()  
{  
    // To avoid storing the connection string in your code,              
    // you can retrieve it from a configuration file.   
  
    // If you have not included "Asynchronous Processing=true" in the  
    // connection string, the command will not be able  
    // to execute asynchronously.  
    return "Data Source=(local);Integrated Security=SSPI;" +  
    "Initial Catalog=AdventureWorks; Asynchronous Processing=true";  
}  
  
private void DisplayStatus(string Text)  
{  
    this.label1.Text = Text;  
}  
  
private void DisplayResults(string Text)  
{  
    this.label1.Text = Text;  
    DisplayStatus("Ready");  
}  
  
private void Form1_FormClosing(object sender, System.Windows.Forms.FormClosingEventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Can't close the form until " +  
        "the pending asynchronous command has completed. Please " +  
        wait...");  
        e.Cancel = true;  
    }  
}  
  
private void button1_Click(object sender, System.EventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Already executing. Please wait until " +  
        "the current query has completed.");  
    }  
    else  
    {  
        SqlCommand command = null;  
        try  
        {  
            DisplayResults("");  
            DisplayStatus("Connecting...");  
            connection = new SqlConnection(GetConnectionString());  
            // To emulate a long-running query, wait for   
            // a few seconds before working with the data.  
            // This command doesn't do much, but that's the point--  
            // it doesn't change your data, in the long run.  
            string commandText =  
                "WAITFOR DELAY '0:0:05';" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint + 1 " +  
                "WHERE ReorderPoint Is Not Null;" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint - 1 " +  
                "WHERE ReorderPoint Is Not Null";  
  
            command = new SqlCommand(commandText, connection);  
            connection.Open();  
  
            DisplayStatus("Executing...");  
            isExecuting = true;  
            // Although it's not required that you pass the   
            // SqlCommand object as the second parameter in the   
            // BeginExecuteNonQuery call, doing so makes it easier  
            // to call EndExecuteNonQuery in the callback procedure.  
            AsyncCallback callback = new AsyncCallback(HandleCallback);  
  
            // Once the BeginExecuteNonQuery method is called,  
            // the code continues--and the user can interact with  
            // the form--while the server executes the query.  
            command.BeginExecuteNonQuery(callback, command);  
  
        }  
        catch (Exception ex)  
        {  
            isExecuting = false;  
            DisplayStatus(   
             string.Format("Ready (last error: {0})", ex.Message));  
            if (connection != null)  
            {  
                connection.Close();  
            }  
        }  
    }  
}  
  
private void HandleCallback(IAsyncResult result)  
{  
    try  
    {  
        // Retrieve the original command object, passed  
        // to this procedure in the AsyncState property  
        // of the IAsyncResult parameter.  
        SqlCommand command = (SqlCommand)result.AsyncState;  
        int rowCount = command.EndExecuteNonQuery(result);  
        string rowText = " rows affected.";  
        if (rowCount == 1)  
        {  
            rowText = " row affected.";  
        }  
        rowText = rowCount + rowText;  
  
        // You may not interact with the form and its contents  
        // from a different thread, and this callback procedure  
        // is all but guaranteed to be running from a different thread  
        // than the form. Therefore you cannot simply call code that   
        // displays the results, like this:  
        // DisplayResults(rowText)  
  
        // Instead, you must call the procedure from the form's thread.  
        // One simple way to accomplish this is to call the Invoke  
        // method of the form, which calls the delegate you supply  
        // from the form's thread.   
        DisplayInfoDelegate del =   
         new DisplayInfoDelegate(DisplayResults);  
        this.Invoke(del, rowText);  
    }  
    catch (Exception ex)  
    {  
        // Because you're now running code in a separate thread,   
        // if you don't handle the exception here, none of your other  
        // code will catch the exception. Because none of your  
        // code is on the call stack in this thread, there's nothing  
        // higher up the stack to catch the exception if you don't   
        // handle it here. You can either log the exception or   
        // invoke a delegate (as in the non-error case in this   
        // example) to display the error on the form. In no case  
        // can you simply display the error without executing a   
        // delegate as in the try block here.   
  
        // You can create the delegate instance as you   
        // invoke it, like this:  
        this.Invoke(new DisplayInfoDelegate(DisplayStatus),  
        String.Format("Ready(last error: {0}", ex.Message));  
    }  
    finally  
    {  
        isExecuting = false;  
        if (connection != null)  
        {  
            connection.Close();  
        }  
    }  
}  
  
private void Form1_Load(object sender, System.EventArgs e)  
{  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    this.FormClosing += new System.Windows.Forms.  
        FormClosingEventHandler(this.Form1_FormClosing);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="570cf-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="570cf-118">See Also</span></span>  
 [<span data-ttu-id="570cf-119">Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="570cf-119">Asynchronous Operations</span></span>](../../../../../docs/framework/data/adonet/sql/asynchronous-operations.md)  
 [<span data-ttu-id="570cf-120">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="570cf-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
