---
title: Bağlantı olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037743"
---
# <a name="connection-events"></a><span data-ttu-id="fdb5f-102">Bağlantı olayları</span><span class="sxs-lookup"><span data-stu-id="fdb5f-102">Connection Events</span></span>
<span data-ttu-id="fdb5f-103">Tüm .NET Framework veri sağlayıcıları **bağlantı** belirlemek için ya da bir veri kaynağından bilgi iletilerini almak için kullanabileceğiniz iki olay nesneleri durumunu bir **bağlantı** sahip değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="fdb5f-104">Aşağıdaki tabloda olaylarını açıklar **bağlantı** nesne.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="fdb5f-105">Olay</span><span class="sxs-lookup"><span data-stu-id="fdb5f-105">Event</span></span>|<span data-ttu-id="fdb5f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdb5f-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fdb5f-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="fdb5f-107">**InfoMessage**</span></span>|<span data-ttu-id="fdb5f-108">Bir veri kaynağından bir bilgi iletisidir döndürüldüğünde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="fdb5f-109">Bilgi iletilerini bir veri kaynağından oluşturulan bir özel durum neden iletileri ' dir.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="fdb5f-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="fdb5f-110">**StateChange**</span></span>|<span data-ttu-id="fdb5f-111">Gerçekleşir, durumunu **bağlantı** değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="fdb5f-112">InfoMessage olayı ile çalışma</span><span class="sxs-lookup"><span data-stu-id="fdb5f-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="fdb5f-113">Bir SQL Server veri kullanarak kaynak uyarıları ve bilgilendirici iletileri alabilirsiniz <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayı <xref:System.Data.SqlClient.SqlConnection> nesne.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="fdb5f-114">16 11 önem derecesi ile veri kaynağından döndürülen hata, bir özel durum oluşturulmasına neden.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="fdb5f-115">Ancak, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay, bir hata ile ilişkili olmayan bir veri kaynağından alınan iletileri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="fdb5f-116">Microsoft SQL Server, söz konusu olduğunda herhangi bir hata önem derecesi 10 veya daha küçük bir bilgi iletisidir olduğu kabul edilir ve kullanılarak yakalanabilir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="fdb5f-117">Daha fazla bilgi için [veritabanı altyapısı hata önem dereceleri](/sql/relational-databases/errors-events/database-engine-error-severities) makalesi.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="fdb5f-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay aldığında bir <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> nesnesini içeren, içinde kendi **hataları** özelliği, veri kaynağından alınan iletileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="fdb5f-119">Sorgulayabilirsiniz **hata** hatanın kaynağının yanı sıra hata sayısı ve ileti metni, bu koleksiyondaki nesneleri.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="fdb5f-120">SQL Server için .NET Framework veri sağlayıcısı ayrıca veritabanı, saklı yordam ve iletinin geldiği satır numarası hakkında ayrıntılı bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="fdb5f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdb5f-121">Example</span></span>  
 <span data-ttu-id="fdb5f-122">Aşağıdaki kod örneği için bir olay işleyicisi eklemek gösterilmektedir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="fdb5f-123">InfoMessages hataları işleme</span><span class="sxs-lookup"><span data-stu-id="fdb5f-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="fdb5f-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay normalde sunucudan gönderilen bilgilendirme ve uyarı iletileri için harekete.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="fdb5f-125">Ancak, gerçek bir hata oluştuğunda, yürütme **ExecuteNonQuery** veya **ExecuteReader** sunucu işlemi başlatan bir yöntemi durdurulamaz ve bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="fdb5f-126">Devam etmek istiyorsanız hataları bağımsız olarak bir komut deyimlerin geri kalanını işlem sunucu tarafından üretilen, Ayarla <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> için `true`.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="fdb5f-127">Bunun yapılması bağlantı ateşlenmesine neden olur <xref:System.Data.SqlClient.SqlConnection.InfoMessage> yerine bir özel durum ve işleme kesintiye hataları için olay.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="fdb5f-128">İstemci uygulaması daha sonra bu olayı işleyin ve hata koşullarını yanıt.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdb5f-129">Sunucunun komut işlenmeden durdurmak neden bir hata 17 veya üzeri önem düzeyine sahip bir özel durum işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="fdb5f-130">Bu durumda, nasıl hata olarak işlenir bağımsız olarak durum <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="fdb5f-131">StateChange olayı ile çalışma</span><span class="sxs-lookup"><span data-stu-id="fdb5f-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="fdb5f-132">**StateChange** bir olay oluşursa, durumu bir **bağlantı** değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="fdb5f-133">**StateChange** olay aldığında <xref:System.Data.StateChangeEventArgs> durumundaki değişikliği belirlemenize olanak sağlayan **bağlantı** kullanarak **OriginalState** ve **CurrentState** özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="fdb5f-134">**OriginalState** özelliği bir <xref:System.Data.ConnectionState> durumunu gösteren numaralandırma **bağlantı** önceki değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="fdb5f-135">**CurrentState** olduğu bir <xref:System.Data.ConnectionState> durumunu gösteren numaralandırma **bağlantı** değiştirmeden sonra.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="fdb5f-136">Aşağıdaki kod örneğinde **StateChange** konsola ileti yazmak için olay olduğunda durumu **bağlantı** değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fdb5f-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdb5f-137">See Also</span></span>  
 [<span data-ttu-id="fdb5f-138">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="fdb5f-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="fdb5f-139">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="fdb5f-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
