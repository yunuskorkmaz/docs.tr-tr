---
title: Bağlantı olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 719e529c7813679f1e927b66e7db0e110714e438
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758170"
---
# <a name="connection-events"></a><span data-ttu-id="de371-102">Bağlantı olayları</span><span class="sxs-lookup"><span data-stu-id="de371-102">Connection Events</span></span>
<span data-ttu-id="de371-103">Tüm .NET Framework veri sağlayıcısı **bağlantı** bilgilendirici iletileri bir veri kaynağından veri almak veya belirlemek için kullanabileceğiniz iki olay nesneleriyle durumunu bir **bağlantı** sahip değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="de371-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="de371-104">Aşağıdaki tabloda olayların açıklanmaktadır **bağlantı** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="de371-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="de371-105">Olay</span><span class="sxs-lookup"><span data-stu-id="de371-105">Event</span></span>|<span data-ttu-id="de371-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de371-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de371-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="de371-107">**InfoMessage**</span></span>|<span data-ttu-id="de371-108">Bir bilgi iletisidir bir veri kaynağından döndürülen oluşur.</span><span class="sxs-lookup"><span data-stu-id="de371-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="de371-109">Bilgilendirici iletileri oluşturulan bir özel durum yol açmamasını iletileri bir veri kaynağından alınan ' dir.</span><span class="sxs-lookup"><span data-stu-id="de371-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="de371-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="de371-110">**StateChange**</span></span>|<span data-ttu-id="de371-111">Oluşur, durumu **bağlantı** değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="de371-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="de371-112">InfoMessage olayı ile çalışma</span><span class="sxs-lookup"><span data-stu-id="de371-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="de371-113">SQL Server veri kaynağı kullanarak bir, uyarılar ve bilgilendirici iletileri alabilirsiniz <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayı <xref:System.Data.SqlClient.SqlConnection> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="de371-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="de371-114">16 11 önem düzeyine sahip veri kaynağından döndürülen hatalar bir özel durum oluşturulmasına neden.</span><span class="sxs-lookup"><span data-stu-id="de371-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="de371-115">Ancak, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay, bir hata ile ilişkili olmayan veri kaynağından alınan iletileri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de371-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="de371-116">Microsoft SQL Server, söz konusu olduğunda herhangi bir hata önem derecesi 10 veya daha az ileti bilgilendirme olarak değerlendirilir ve kullanılarak yakalanabilir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.</span><span class="sxs-lookup"><span data-stu-id="de371-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="de371-117">Daha fazla bilgi için SQL Server Books Online'da "Hata iletisi önem düzeyleri" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="de371-117">For more information, see the "Error Message Severity Levels" topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="de371-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olayı aldığı bir <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> nesnesini içeren, buna onun **hataları** özelliği, veri kaynağından alınan iletileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="de371-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="de371-119">Sorgulayabileceğiniz **hata** hatanın kaynağını yanı sıra, hata numarası ve ileti metni için bu koleksiyonundaki nesneleri.</span><span class="sxs-lookup"><span data-stu-id="de371-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="de371-120">SQL Server için .NET Framework veri sağlayıcısı ayrıca veritabanı, saklı yordam ve iletinin geldiği satır numarası hakkında ayrıntılı bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="de371-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="de371-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="de371-121">Example</span></span>  
 <span data-ttu-id="de371-122">Aşağıdaki kod örneği için bir olay işleyicisi ekleme gösterir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.</span><span class="sxs-lookup"><span data-stu-id="de371-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="de371-123">InfoMessages hataları işleme</span><span class="sxs-lookup"><span data-stu-id="de371-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="de371-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay normalde sunucudan gönderilen bilgi ve uyarı iletileri için kov.</span><span class="sxs-lookup"><span data-stu-id="de371-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="de371-125">Ancak, gerçek bir hata oluştuğunda, yürütülmesi **ExecuteNonQuery** veya **ExecuteReader** sunucu işlemi başlatan yöntem durdurulamaz ve bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="de371-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="de371-126">Devam etmek istiyorsanız hataları bağımsız olarak bir komut deyimlerinde kalan işleme sunucu tarafından üretilen, Ayarla <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> için `true`.</span><span class="sxs-lookup"><span data-stu-id="de371-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="de371-127">Bunun yapılması neden tetiklenecek bağlantı <xref:System.Data.SqlClient.SqlConnection.InfoMessage> bir özel durum atma ve işleme kesintiye yerine hataları için olay.</span><span class="sxs-lookup"><span data-stu-id="de371-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="de371-128">İstemci uygulaması bu olayı işlemek ve hata koşullarını yanıt.</span><span class="sxs-lookup"><span data-stu-id="de371-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de371-129">Komut işlemeyi durdur sunucuya neden olan hata 17 veya üstü önem düzeyine sahip bir özel durum olarak ele alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="de371-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="de371-130">Bir özel nasıl hata olarak ele alınır bağımsız olarak bu durumda, durum <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.</span><span class="sxs-lookup"><span data-stu-id="de371-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="de371-131">StateChange olay ile çalışma</span><span class="sxs-lookup"><span data-stu-id="de371-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="de371-132">**StateChange** olayı oluşur, durumu bir **bağlantı** değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="de371-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="de371-133">**StateChange** olayı aldığı <xref:System.Data.StateChangeEventArgs> durumundaki değişikliği belirlemek etkinleştirme **bağlantı** kullanarak **OriginalState** ve **CurrentState** özellikleri.</span><span class="sxs-lookup"><span data-stu-id="de371-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="de371-134">**OriginalState** özelliği bir <xref:System.Data.ConnectionState> durumunu belirten numaralandırma **bağlantı** önce onu değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="de371-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="de371-135">**CurrentState** olan bir <xref:System.Data.ConnectionState> durumunu belirten numaralandırma **bağlantı** onu değiştikten sonra.</span><span class="sxs-lookup"><span data-stu-id="de371-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="de371-136">Aşağıdaki kod örneğinde **StateChange** konsoluna bir ileti yazmak için olay zaman durumunu **bağlantı** değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="de371-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="de371-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de371-137">See Also</span></span>  
 [<span data-ttu-id="de371-138">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="de371-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="de371-139">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="de371-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
